
---

# 🌐 APACHE VIRTUAL HOSTING (FULL LAB)

👉 Goal:
**Ek hi server par multiple websites host karna**

---

# 🧩 1️⃣ Install Apache

```bash
yum install httpd -y
```

Start service:

```bash
systemctl start httpd
systemctl enable httpd
```

---

# 📂 2️⃣ Create Website Directories

```bash
mkdir -p /var/www/site1
mkdir -p /var/www/site2
```

---

# 📝 3️⃣ Create Test Pages

```bash
echo "Welcome to Site1" > /var/www/site1/index.html
echo "Welcome to Site2" > /var/www/site2/index.html
```

---

# ⚙️ 4️⃣ Configure Virtual Hosts


✔ Correct file:

```bash
vi /etc/httpd/conf/httpd.conf
```

👉 End me add karo:

```apache
<VirtualHost *:80>
    ServerAdmin admin@site1.com
    DocumentRoot /var/www/site1
    ServerName site1.com
    ErrorLog logs/site1-error_log
    CustomLog logs/site1-access_log common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin admin@site2.com
    DocumentRoot /var/www/site2
    ServerName site2.com
    ErrorLog logs/site2-error_log
    CustomLog logs/site2-access_log common
</VirtualHost>
```

---

# 🔑 5️⃣ Add Entries in Hosts File (IMPORTANT)

```bash
vi /etc/hosts
```

Add:

```bash
127.0.0.1   site1.com
127.0.0.1   site2.com
```

---

# 🔄 6️⃣ Restart Apache

```bash
systemctl restart httpd
```

---

# 🌐 7️⃣ Test in Browser

Open browser:

```
http://site1.com
http://site2.com
```

👉 Dono alag pages open honge ✔

---
