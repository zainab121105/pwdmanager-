# pwdmanager-
from cryptography.fernet import Fernet
import os
def view():
    with open("passwords.txt","r") as p:
        for line in p.readlines():
            data=line.rstrip()
        uname,password=data.split("|")
        print("User Name: "+uname+"\n"+"Password: "+fer.decrypt(password.encode()).decode())

def add():
    user_name=input("Enter your username: ")
    pwd=input("Enter your password: ")
    with open("passwords.txt","a") as f:
        f.write(user_name+"|"+fer.encrypt(pwd.encode()).decode())

def delete():
    if os.path.exists("passwords.txt"):
        os.remove("passwords.txt")
    else:
        print("Doesnot exists")

def key_load():
    file=open("key.key","rb")
    key=file.read()
    file.close()
    return key

key=key_load()
fer=Fernet(key)

while True:
    mode=input("Choose your mode of interest: (view/add/delete/q)")
    if mode=="view":
        view()
    elif mode=="add":
        add()
    elif mode=="delete":
        delete()
    else:
        print("Invalid Mode")
        quit()

