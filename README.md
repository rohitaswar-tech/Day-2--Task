# AWS EC2 – Day 2 Tasks

This repository contains evidence and notes for the Day 2 AWS EC2 lab, covering vertical scaling, Windows EC2 with RDP, and Linux EC2 with PuTTY/PuTTYgen.

## 📋 Overview

| Task | Topic | Evidence |
|------|-------|----------|
| 1 | Vertical Scaling of EC2 | `screenshots/Task1_1.png` – `Task1_4.png` |
| 2 | Windows EC2 + RDP | `screenshots/Task2_1.png`, `Task2_2.png`, `Task2_2_1.png` |
| 3 | Linux EC2 + PuTTYgen + PuTTY | `screenshots/Task3_1.png` – `Task3_4.png` |

---

## Task 1 – Vertically Scale an EC2 Instance

**Objective:** Vertically scale an existing EC2 instance (`exam`, instance type `t3.micro`) to a larger instance type and verify the change.

**Steps performed:**
1. Identified the running `t3.micro` instance (`i-0b5b0274be95e5e2b`, named **exam**) and recorded its instance ID. *(Task1_1.png)*
2. Stopped the instance — required before the instance type can be changed. *(Task1_2.png)*
3. Used **Actions → Instance settings → Change instance type** from the EC2 console. *(Task1_3.png)*
4. Changed the instance type, and confirmed the change with the **"Instance type changed successfully"** banner — instance now shows type `c7i-flex.large`. *(Task1_4.png)*

📸 **Evidence:**
- `screenshots/Task1_1.png` – Original instance running as t3.micro
- `screenshots/Task1_2.png` – Instance stopped
- `screenshots/Task1_3.png` – Change instance type menu
- `screenshots/Task1_4.png` – Updated instance type confirmed

---

## Task 2 – Launch a Windows EC2 Instance and Connect Using RDP

**Objective:** Launch a Windows EC2 instance and connect to it using RDP.

**Steps performed:**
1. Launched a new Windows EC2 instance (**Task2**, `i-0867d94276e3327f9`, t3.micro) and confirmed it passed status checks (3/3). *(Task2_1.png)*
2. Configured the security group to allow RDP (TCP port 3389) from the permitted source.
3. Retrieved the Windows administrator credentials via the EC2 console.
4. Connected via Remote Desktop Connection using the instance's public IPv4 address (`3.88.166.79`) and successfully reached the Windows desktop. *(Task2_2.png, Task2_2_1.png)*

📸 **Evidence:**
- `screenshots/Task2_1.png` – Windows instance running, status checks passed
- `screenshots/Task2_2.png` – Successful RDP session (full window)
- `screenshots/Task2_2_1.png` – Successful RDP session (desktop view)

> ⚠️ No passwords or private keys are visible in the screenshots.

---

## Task 3 – Connect to a Linux EC2 Instance Using PuTTYgen and PuTTY

**Objective:** Launch a Linux EC2 instance, convert the `.pem` key to `.ppk` using PuTTYgen, and connect via PuTTY (SSH).

**Steps performed:**
1. Launched a new Linux EC2 instance (**linuxlab**, `i-0c867fbb65b4d3479`, t3.micro, Amazon Linux 2023) and confirmed it passed status checks. *(Task3_1.png)*
2. Configured the security group to allow SSH (TCP port 22) from the permitted source.
3. Converted the downloaded `.pem` key to `.ppk` format using PuTTYgen and saved it as `linux-key.ppk`.
4. Opened PuTTY, entered the instance's public IPv4 address (`54.226.226.62`) on port 22 with SSH connection type, and saved the session as `aws-linux`. *(Task3_2.png)*
5. Under **Connection → SSH → Auth → Credentials**, selected the `.ppk` private key file for authentication. *(Task3_3.png)*
6. Started the session, logged in as `ec2-user`, and got a working command-line session confirming the SSH connection to the Amazon Linux instance. *(Task3_4.png)*

📸 **Evidence:**
- `screenshots/Task3_1.png` – Linux instance running, status checks passed
- `screenshots/Task3_2.png` – PuTTY session configuration (host & port)
- `screenshots/Task3_3.png` – PuTTY private key (.ppk) selected for authentication
- `screenshots/Task3_4.png` – Successful SSH terminal session as ec2-user

> ⚠️ Private key contents are not visible in the screenshot.

---

## 🔐 Security Notes

- No passwords, private keys, or other sensitive credentials are included in any screenshot.
- RDP access is restricted to TCP port 3389 from the permitted source IP only.
- SSH access is restricted to TCP port 22 from the permitted source IP only.
- Resources are stopped/terminated after task completion to avoid unnecessary AWS charges.

## ✅ Submission Checklist

- [x] Task 1 completed – EC2 vertically scaled and verified
- [x] Task 1 screenshots attached
- [x] Task 2 completed – Windows EC2 launched and connected through RDP
- [x] Task 2 screenshots attached
- [x] Task 3 completed – Linux EC2 launched, `.pem` converted to `.ppk`, connected using PuTTY
- [x] Task 3 screenshots attached
- [x] No private keys, passwords, or sensitive credentials visible in screenshots

---

## 🛠️ Tools Used

- AWS Management Console (EC2)
- Remote Desktop Connection (RDP client)
- PuTTY
- PuTTYgen
