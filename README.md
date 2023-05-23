# CodeClause_URLshortner
import pyperclip
import pyshorteners
from tkinter import *



root=Tk()

#set the geometry
#root.geometry("400*200")

#give a title
root.title("url shortener")

#set a background color
root.configure(bg="#49A")

#take 2 string variable for keeping long and short url
url = stringvar()
url_address = stringvar()

#define 2 functions for shortening url and copy url
def urlshortener():
    urladdress = url.get()
    url_short=pyshorteners.Shortener().tinyurl.short(urladdress)
    url_address.set(url_short)

def copyurl():
    url_short=url_address.get()
    pyperclip.copy(url_short)

label(root , text="my url shotener",font="poppins").pack(pady=10)
entry(root , textvariable=url).pack(pady=5)
button(root , text="generate short url",command=urlshortener).pack(pady=7)
entry(root ,textvariable=url_address).pack(pady=5)
button(root, text="copy url",command=copyurl).pack(pady=5)

root.mainloop()
