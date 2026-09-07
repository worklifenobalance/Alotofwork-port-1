#งานสำหลับส่งครู by ณัฐวัตร พลายอยู่วงษ์
import tkinter as tk
from tkinter import ttk, messagebox

def วาดสไลด์(shape):
    canvas.delete("all")
    x = -220

    def animate():
        nonlocal x
        canvas.delete("all")

        if shape == "สี่เหลี่ยมผืนผ้า":
            canvas.create_rectangle(x,60,x+180,140,fill="skyblue",outline="blue",width=3)
        elif shape == "สี่เหลี่ยมจัตุรัส":
            canvas.create_rectangle(x+30,40,x+150,160,fill="plum",outline="purple",width=3)
        elif shape == "วงกลม":
            canvas.create_oval(x+15,30,x+165,180,fill="lightgreen",outline="green",width=3)
        elif shape == "สามเหลี่ยม":
            canvas.create_polygon(x+85,30,x,170,x+170,170,fill="orange",outline="darkorange",width=3)
        elif shape == "สี่เหลี่ยมคางหมู":
            canvas.create_polygon(x+50,40,x+140,40,x+190,160,x,160,
                                  fill="tomato",outline="red",width=3)
        elif shape == "สี่เหลี่ยมด้านขนาน":
            canvas.create_polygon(x+40,40,x+170,40,x+140,160,x+10,160,
                                  fill="khaki",outline="goldenrod",width=3)

        if x < 40:
            x += 10
            root.after(15, animate)

    animate()

def change_labels(event=None):
    s = combo.get()
    draw_shape(s)

    for e in (e1,e2,e3):
        e.delete(0,tk.END)

    if s=="สี่เหลี่ยมผืนผ้า":
        l1.config(text="ความกว้าง"); l2.config(text="ความยาว")
        l2.grid(); e2.grid()
        l3.grid_remove(); e3.grid_remove()

    elif s=="สี่เหลี่ยมจัตุรัส":
        l1.config(text="ความยาวด้าน")
        l2.grid_remove(); e2.grid_remove()
        l3.grid_remove(); e3.grid_remove()

    elif s=="วงกลม":
        l1.config(text="รัศมี")
        l2.grid_remove(); e2.grid_remove()
        l3.grid_remove(); e3.grid_remove()

    elif s=="สามเหลี่ยม":
        l1.config(text="ฐาน"); l2.config(text="สูง")
        l2.grid(); e2.grid()
        l3.grid_remove(); e3.grid_remove()

    elif s=="สี่เหลี่ยมคางหมู":
        l1.config(text="ฐานบน"); l2.config(text="ฐานล่าง"); l3.config(text="สูง")
        l2.grid(); e2.grid()
        l3.grid(); e3.grid()

    elif s=="สี่เหลี่ยมด้านขนาน":
        l1.config(text="ฐาน"); l2.config(text="สูง")
        l2.grid(); e2.grid()
        l3.grid_remove(); e3.grid_remove()

def draw_shape(shape):
    วาดสไลด์(shape)

def calculate():
    try:
        s = combo.get()

        if s=="สี่เหลี่ยมผืนผ้า":
            a=float(e1.get()); b=float(e2.get())
            area=a*b
            result.config(text=f"พื้นที่ = {area:.2f}\nเส้นรอบรูป = {2*(a+b):.2f}")

        elif s=="สี่เหลี่ยมจัตุรัส":
            a=float(e1.get())
            area=a*a
            result.config(text=f"พื้นที่ = {area:.2f}\nเส้นรอบรูป = {4*a:.2f}")

        elif s=="วงกลม":
            r=float(e1.get())
            area=3.14159*r*r
            result.config(text=f"พื้นที่ = {area:.2f}")

        elif s=="สามเหลี่ยม":
            b=float(e1.get()); h=float(e2.get())
            area=0.5*b*h
            result.config(text=f"พื้นที่ = {area:.2f}")

        elif s=="สี่เหลี่ยมคางหมู":
            t=float(e1.get()); b=float(e2.get()); h=float(e3.get())
            area=((t+b)*h)/2
            result.config(text=f"พื้นที่ = {area:.2f}")

        elif s=="สี่เหลี่ยมด้านขนาน":
            b=float(e1.get()); h=float(e2.get())
            area=b*h
            result.config(text=f"พื้นที่ = {area:.2f}")

        history.insert(tk.END,f"{s} = {area:.2f}")
    except:
        messagebox.showerror("ผิดพลาด","กรุณากรอกตัวเลขให้ถูกต้อง")

def clear_data():
    for e in (e1,e2,e3):
        e.delete(0,tk.END)
    result.config(text="พื้นที่ = 0")

root=tk.Tk()
root.title("📐 โปรแกรมคำนวณพื้นที่รูปทรง")
root.geometry("500x800")
root.resizable(True,True)
root.configure(bg="#EAF6FF")

tk.Label(root,text="📐 โปรแกรมคำนวณพื้นที่รูปทรง",
         font=("Tahoma",18,"bold"),bg="#EAF6FF").pack(pady=10)

frame=tk.LabelFrame(root,text="ข้อมูลการคำนวณ")
frame.pack(fill="x",padx=15,pady=5)

tk.Label(frame,text="เลือกรูปทรง").grid(row=0,column=0,padx=5,pady=5)

combo=ttk.Combobox(frame,state="readonly",values=[
"สี่เหลี่ยมผืนผ้า","สี่เหลี่ยมจัตุรัส","วงกลม",
"สามเหลี่ยม","สี่เหลี่ยมคางหมู","สี่เหลี่ยมด้านขนาน"])
combo.grid(row=0,column=1)
combo.current(0)

l1=tk.Label(frame,text="ความกว้าง"); l1.grid(row=1,column=0,pady=5)
e1=tk.Entry(frame); e1.grid(row=1,column=1,pady=5)

l2=tk.Label(frame,text="ความยาว"); l2.grid(row=2,column=0,pady=5)
e2=tk.Entry(frame); e2.grid(row=2,column=1,pady=5)

l3=tk.Label(frame,text="")
l3.grid(row=3,column=0,pady=5)
e3=tk.Entry(frame)
e3.grid(row=3,column=1,pady=5)
l3.grid_remove(); e3.grid_remove()

combo.bind("<<ComboboxSelected>>",change_labels)

tk.Button(root,text="🧮 คำนวณ",command=calculate).pack(pady=5)
tk.Button(root,text="🗑 ล้างข้อมูล",command=clear_data).pack()

result=tk.Label(root,text="พื้นที่ = 0",font=("Tahoma",14,"bold"),bg="#EAF6FF")
result.pack(pady=10)

canvas=tk.Canvas(root,width=260,height=200,bg="white")
canvas.pack(pady=10)
draw_shape("สี่เหลี่ยมผืนผ้า")

tk.Label(root,text="📜 ประวัติการคำนวณ",bg="#EAF6FF",
         font=("Tahoma",11,"bold")).pack()

history=tk.Listbox(root,height=5)
history.pack(fill="x",padx=15)

guide=tk.LabelFrame(root,text="📖 คู่มือการใช้งาน")
guide.pack(fill="both",expand=True,padx=15,pady=10)

scroll=tk.Scrollbar(guide)
scroll.pack(side="right",fill="y")

text=tk.Text(guide,wrap="word",yscrollcommand=scroll.set)
text.pack(fill="both",expand=True)
scroll.config(command=text.yview)

text.insert("1.0","""
1. เลือกรูปทรง
2. กรอกข้อมูล
3. กดปุ่มคำนวณ
รองรับ:
• สี่เหลี่ยมผืนผ้า
• สี่เหลี่ยมจัตุรัส
• วงกลม
• สามเหลี่ยม
• สี่เหลี่ยมคางหมู
• สี่เหลี่ยมด้านขนาน
จัดทำโดย Nattawat prayoowong No.17 M.6/3
""")
text.config(state="disabled")

root.mainloop()
