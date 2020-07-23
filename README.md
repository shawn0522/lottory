# lottory
lottery program can generate six numbers
import requests
import random
import time
#window = tk.Tk()
#window.title('樂透抽獎程式')
#window.geometry('500x300')
#var = tk.StringVar()
#canvas = tk.Canvas(window, bg='green', height=200, width=500)
#視窗
jotain = []
i = [50]
j = 1
lot = []
from bs4 import BeautifulSoup
response = requests.get("http://www.9800.com.tw/trend.asp")
html_doc = response.text 
soup = BeautifulSoup(response.text, "html.parser")
a_tags = soup.find("table",bordercolor="#cccccc").find_all("td",style="background-color:#FF3366;color:#FFFFFF")

def aa():
	label_img['text'] = "系統演算中. . ."
	root.update()
	time.sleep(5)
	qq()

def qq():
	list.clear(lot)
	a_tags777 = random.sample(a_tags,6)
	for tag in a_tags777:
		print(tag.text.strip())
		lot.append(tag.text.strip())
	label_img['text'] = lot

#	print(lot,end="")


# print("離開請輸入 Y 重骰請輸入 N \n")
# a = input()
# if (a == 'Y'):
#  break
# elif (a == 'y'):
#  break
# elif (a == 'N'):
#  print("-----------------------------------------\n|為您產生新的號碼|\n-----------------------------------------")
# elif (a == 'n'):
#  print("-----------------------------------------\n|為您產生新的號碼|\n-----------------------------------------")
  
#視窗


#image_file = tk.PhotoImage(file='A5.gif') 
#image = canvas.create_image(300, 0, anchor='n',image=image_file) 
#canvas.pack()

'''
import tkinter as tk
from PIL import ImageTk, Image

root = tk.Tk()
#背景
canvas = tk.Canvas(root,width=1500,height=1000,bd=0, highlightthickness=0 ,)
imgpath = 'gold.png'
img = Image.open(imgpath)
photo = ImageTk.PhotoImage(img)
canvas.create_image(200, 200, image=photo)
canvas.pack()
canvas.pack()
imagetest = tk.PhotoImage(file="btm.gif")

b = tk.Button(root,image=imagetest, width=400, height=100, command=qq)
b.pack()

root.mainloop()


import tkinter
from tkinter import *

root = tkinter.Tk()
root.configure(background='#16e116')
root.title('自動預測樂透彩程式')
root.geometry('700x500')

photo = PhotoImage(file='gold.png')

w = Label(root, image=photo)
text = Label(root, text="Hello world!",font=("Courier",30))

w.grid(row=0, column=0)
text.grid(row=0, column=0)
'''

 
from tkinter import *
from tkinter import font as tkFont

root = Tk()
root.geometry('800x600')
root.title('樂透抽獎程式')
helv36 = tkFont.Font(family='Helvetica', size=30, weight='bold')

img_png = PhotoImage(file = 'gold.png')


label_img = Label(root, image = img_png ,compound=CENTER, text = "以下為您預測的高機率出現號碼為:")
label_img['font'] = helv36
label_img.pack()
helv36 = tkFont.Font(family='Helvetica', size=36, weight='bold')
imagetest = PhotoImage(file="btm.png")


b = Button(root,image=imagetest, width=400, height=100, command=aa , text="按此預測號碼",compound=CENTER)
b['font'] = helv36
b.pack()


mainloop()
