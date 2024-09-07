
from tkinter import *
import tkinter
from PIL import ImageTk, Image


root=Tk()
root.title("BITWISE OPERATION")
root.geometry('1000x600')
root.maxsize(1000,600)
font1=("Times",14,"bold")
font2=("Times",13,"bold")

res = 0  
tfprs = "" 
def and1(a,b):
    global res
    res = int(a and b)
def or1(a,b):
    global res
    res  = int(a | b)
def not1(a):
    global res
    res = int(not a)
def xor1(a,b):
    global res
    res = int((a and not b) or (not a and b))
def result(event=None):
    global root,res,E3
    text = StringVar()
    E3=Entry(f2,textvariable=text,bd=5)
    E3.place(x=600,y=400)
    text.set(str(res))
def selected():
    global tfprs
    tfprs = var.get()
def exit1(root):
    root.destroy()
def exit2(root):
    root.destroy()
def expl(a,b):
    global root,tfprs,res
    binary1 = StringVar()
    binary2 = StringVar()
    top1=tkinter.Toplevel(root)
    top1.geometry('1000x600')
    top1.title("EXPLANATION")
    
    f3=Frame(top1,height=600,width=1000)
    f3.propagate(0)
    f3.pack(side='top')

    c= Canvas(f3,height=600,width=1000,background='white')
    c.pack()
    p3= ImageTk.PhotoImage(Image.open("front1.jpg").resize((400,600)))
    c.create_image(0,0,image=p3, anchor=NW)

    value1 = IntVar()
    l1=Label(top1,text="Number 1:", font=font1)
    l1.place(x=450,y=100)
    e1=Entry(top1,textvariable = value1,bd=5)
    value1.set(a)
    e1.place(x=650,y=100)
    e3=Entry(top1,textvariable = binary1,bd=5)
    l3=Label(top1,text="Binary Number 1:", font=font1)
    l3.place(x=450,y=250)
    binary1.set(format(a,'b'))
    e3.place(x=650,y=250)

    value2 = IntVar()
    l2=Label(top1,text="Number 2:", font=font1)
    l2.place(x=450,y=150)
    e2=Entry(top1,textvariable = value2,bd=5)
    value2.set(b)
    e2.place(x=650,y=150)
    l4=Label(top1,text="Binary Number 2:", font=font1)
    l4.place(x=450,y=300)
    e4=Entry(top1,textvariable = binary2,bd=5)
    binary2.set(format(b,'b'))
    e4.place(x=650,y=300)
    
    l5=Label(top1,text="Selected operator:", font=font1) 
    l5.place(x=450,y=350)
    operator = StringVar()
    e5=Entry(top1,textvariable = operator,bd=5)
    operator.set(tfprs)
    operator.set(tfprs)
    e5.place(x=650,y=350)
    dres = IntVar()
    l6=Label(top1,text="Decimal Result:", font=font1)
    l6.place(x=450,y=400)
    e6=Entry(top1,textvariable = dres ,bd=5)
    dres.set(res)
    e6.place(x=650,y=400)
    b1=tkinter.Button(top1, font=font1,text="EXIT",foreground='white',bg='#8b1c13',command=lambda root=top1:exit2(top1),width=20,border=10)
    b1.place(x=700,y=500)
    root.mainloop()
def dotwo(a,b):
    selected()
    expl(a,b)        


#frame 1
def des_f1():
    f1.destroy()

f1=Frame(root,height=600,width=1000, background='black')    #creating frame 1
f1.propagate(0)
f1.pack(side='top')

p1= ImageTk.PhotoImage(Image.open("front1.jpg").resize((1000,600)))     #background image
label = Label(f1, image = p1)
label.pack()

Button(f1,text="START",font=font1,foreground='white',command=des_f1,bg='#8b1c13',width=20,border=10).place(x=360,y=450)


#frame 2
f2=Frame(root,height=600,width=1000)
f2.propagate(0)
f2.pack(side='top')

c= Canvas(f2,height=600,width=1000,background='white')
c.pack()
p3= ImageTk.PhotoImage(Image.open("front1.jpg").resize((400,600)))
c.create_image(0,0,image=p3, anchor=NW)

num1 = IntVar()
L1=Label(f2,text="Number 1:", font=font1)
L1.place(x=450,y=100)
E1=Entry(f2,textvariable = num1,bd=5)
num1.set(1)
E1.place(x=600,y=100)
num2 = IntVar()
L2=Label(f2,text="Number 2:", font=font1)
L2.place(x=450,y=150)
E2=Entry(f2,textvariable =num2,bd=5)
num2.set(1)
E2.place(x=600,y=150)
var=StringVar()

R1=Radiobutton(f2,text="AND",variable=var,value="AND",command=lambda: and1(int(E1.get()),int(E2.get())))
R1.place(x=450,y=200)
R2=Radiobutton(f2,text="OR",variable=var,value="OR",command=lambda: or1(int(E1.get()),int(E2.get())))
R2.place(x=600,y=200)
R3=Radiobutton(f2,text="NOT",variable=var,value="NOT",command=lambda: not1(int(E1.get())))
R3.place(x=450,y=250)
R4=Radiobutton(f2,text="XOR",variable=var,value="XOR",command=lambda: xor1(int(E1.get()),int(E2.get())))
R4.place(x=600,y=250)
label=Label(root)

b1= Button(f2,text="RESULT",font=font1,foreground='black',command=lambda: [result()],width=12,border=6)
b1.place(x=450,y=300)
b2= Button(f2,text="EXPLANATION",font=font1,foreground='black',command=lambda:dotwo(int(E1.get()),int(E2.get())),width=14,border=6)
b2.place(x=750, y=300)
b3= Button(f2,text="EXIT",font=font1,foreground='white',bg='#8b1c13',command=lambda root=root:exit1(root),width=20,border=10)
b3.place(x=575,y=500)
L3=Label(f2,text="Result is:", font=font1)
L3.place(x=450,y=400)
E3=Entry(f2,bd=5)
E3.place(x=600,y=400)


root.mainloop()    