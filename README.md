import tkinter as tk
from tkinter import messagebox

def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

def find_primes():
    try:
        start = int(entry_start.get())
        end = int(entry_end.get())
        primes = [str(num) for num in range(start, end + 1) if is_prime(num)]
        
        if primes:
            result = "اعداد اول در بازه {} تا {}:\n".format(start, end) + ", ".join(primes)
        else:
            result = "در این بازه عدد اولی یافت نشد."
        
        messagebox.showinfo("نتیجه", result)
    except ValueError:
        messagebox.showerror("خطا", "لطفا اعداد معتبر وارد کنید.")

# رابط گرافیکی
root = tk.Tk()
root.title("یافتن اعداد اول در بازه")

tk.Label(root, text="عدد شروع:").grid(row=0, column=0, padx=5, pady=5)
entry_start = tk.Entry(root)
entry_start.grid(row=0, column=1, padx=5, pady=5)

tk.Label(root, text="عدد پایان:").grid(row=1, column=0, padx=5, pady=5)
entry_end = tk.Entry(root)
entry_end.grid(row=1, column=1, padx=5, pady=5)

btn_find = tk.Button(root, text="یافتن اعداد اول", command=find_primes)
btn_find.grid(row=2, column=0, columnspan=2, pady=10)

root.mainloop()
