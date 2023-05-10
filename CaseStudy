# Bảng hệ thống quản lí nhân viên gồm các chức năng thêm, tìm, xóa, cập nhật , in ra tất cả thông tin của nhân viên gồm
# mã ID, Tên, Ngày sinh, Quê quán
import tkinter as tk
from tkinter import messagebox
#định nghĩa lớp employee để lưu trữ thông tin một nhân viên, init khởi tạo thuộc tính của nhân viên. 
# hàm Info để in thông tin của nhân viên ra màn hình 
class Employee:
    def __init__(self, id, name, dob, hometown):
        self.id = id
        self.name = name
        self.dob = dob
        self.hometown = hometown

    def info(self):
        print(f"ID: {self.id}")
        print(f"Name: {self.name}")
        print(f"Date of birth: {self.dob}")
        print(f"Hometown: {self.hometown}")
#tạo lớp (class) EmployeeList để quản lý danh sách nhân viên
class EmployeeList:
    def __init__(self):
        self.employees = []

    def add_employee(self, employee):
        self.employees.append(employee)

    def update_employee(self, id, name, dob, hometown):
        for employee in self.employees:
            if employee.id == id:
                employee.name = name
                employee.dob = dob
                employee.hometown = hometown
                return True
        return False

    def delete_employee(self, id):
        for employee in self.employees:
            if employee.id == id:
                self.employees.remove(employee)
                return True
        return False

    def find_employee(self, id):
        for employee in self.employees:
            if employee.id == id:
                return employee
        return None

    def get_all_employees(self):
        return self.employees
Lớp Application này tạo ra một ứng dụng GUI sử dụng thư viện tkinter trong Python.
class Application(tk.Frame):
    def __init__(self, master=None):
        super().__init__(master)
        self.master = master
        self.master.title("Hệ thống quản lý nhân viên công ty")
        self.employee_list = EmployeeList()
        self.create_widgets()
#Phương thức create_widgets được sử dụng để tạo ra các thành phần giao diện người dùng, tạo ra một ô văn bản (Text) 
#để hiển thị kết quả.
    def create_widgets(self):
        tk.Label(self.master, text="ID").grid(row=0, column=0)
        tk.Label(self.master, text="Tên").grid(row=1, column=0)
        tk.Label(self.master, text="Ngày Sinh").grid(row=2, column=0)
        tk.Label(self.master, text="Quê quán").grid(row=3, column=0)

        self.id_entry = tk.Entry(self.master)
        self.id_entry.grid(row=0, column=1)

        self.name_entry = tk.Entry(self.master)
        self.name_entry.grid(row=1, column=1)

        self.dob_entry = tk.Entry(self.master)
        self.dob_entry.grid(row=2, column=1)

        self.hometown_entry = tk.Entry(self.master)
        self.hometown_entry.grid(row=3, column=1)

        tk.Button(self.master, text="Thêm", command=self.add_employee).grid(row=4, column=0)
        tk.Button(self.master, text="Cập nhật", command=self.update_employee).grid(row=4, column=1)
        tk.Button(self.master, text="Xóa", command=self.delete_employee).grid(row=4, column=2)
        tk.Button(self.master, text="Tìm Kiếm", command=self.find_employee).grid(row=5, column=0)
        tk.Button(self.master, text="Hiển thị tất cả", command=self.show_all_employees).grid(row=5, column=1)

        self.result_text = tk.Text(self.master, height=30, width=40)
        self.result_text.grid(row=6, column=0, columnspan=3)

    def add_employee(self):
        id = self.id_entry.get()
        name = self.name_entry.get()
        dob = self.dob_entry.get()
        hometown = self.hometown_entry.get()
        employee = Employee(id, name, dob, hometown)
        self.employee_list.add_employee(employee)
        self.result_text.insert(tk.END, f"Added employee with ID {id}\n")

    def update_employee(self):
        id = self.id_entry.get()
        name = self.name_entry.get()
        dob = self.dob_entry.get()
        hometown = self.hometown_entry.get()
        if self.employee_list.update_employee(id, name, dob, hometown):
            self.result_text.insert(tk.END, f"Updated employee with ID {id}\n")
        else:
            self.result_text.insert(tk.END, f"Employee with ID {id} not found\n")

    def delete_employee(self):
        id = self.id_entry.get()
        if self.employee_list.delete_employee(id):
            self.result_text.insert(tk.END, f"Deleted employee with ID {id}\n")
        else:
            self.result_text.insert(tk.END, f"Employee with ID {id} not found\n")

    def find_employee(self):
        id = self.id_entry.get()
        employee = self.employee_list.find_employee(id)
        if employee:
            self.result_text.insert(tk.END, f"Found employee with ID {id}\n")
            self.result_text.insert(tk.END, f"Name: {employee.name}\n")
            self.result_text.insert(tk.END, f"Date of birth: {employee.dob}\n")
            self.result_text.insert(tk.END, f"Hometown: {employee.hometown}\n")
        else:
            self.result_text.insert(tk.END, f"Employee with ID {id} not found\n")

    def show_all_employees(self):
        employees = self.employee_list.get_all_employees()
        self.result_text.delete("1.0", tk.END)
        for employee in employees:
            self.result_text.insert(tk.END, f"ID: {employee.id}\n")
            self.result_text.insert(tk.END, f"Name: {employee.name}\n")
            self.result_text.insert(tk.END, f"Date of birth: {employee.dob}\n")
            self.result_text.insert(tk.END, f"Hometown: {employee.hometown}\n\n")
root = tk.Tk()
app = Application(master=root)
app.mainloop()    
