<h1 align="center">Phishing and Social Engineering Analysis Project</h1>

<p align="center">
  <b></b> Simulating a Fake Login Page to Capture User Credentials - XAMPP, PHP & MySQL
</p>

<p align="center">
  📄 <b>Download PDF Documentation:</b><br>
  [ EN ] <a href="https://github.com/radu-hatos/Phishing_and_Social_Engineering_Analysis_Project/blob/main/Phishing_and_Social_Engineering_Analysis_Project.pdf"><b>[ English Version PDF ]</b></a><br>
  [ ES ] <a href="https://github.com/radu-hatos/Phishing_and_Social_Engineering_Analysis_Project/blob/main/Analisis_Practico_de_Tecnicas_de_Phishing_e_Ingenieria_Social.pdf"><b>[ Versión en Español PDF ]</b></a>
</p>

<hr>

## 📋 Index

- [1. Introduction](#1-introduction)
- [2. Objective](#2-objective)
- [3. Environment](#3-environment)
- [4. Work Performed](#4-work-performed)
  - [4.1 XAMPP Setup and Database Preparation](#41-xampp-setup-and-database-preparation)
  - [4.2 Cloning the Legitimate Login Page](#42-cloning-the-legitimate-login-page)
  - [4.3 Building the Credential-Capture Script (server.php)](#43-building-the-credential-capture-script-serverphp)
  - [4.4 Test and Result](#44-test-and-result)
  - [4.5 Delivery and the Social-Engineering Vector](#4.5-delivery-and-the-social-engineering-vector)
- [5. Skills Demonstrated](#5-skills-demonstrated)
- [6. Tools Used](#6-tools-used)

---

## 1. Introduction

This is an ethical-hacking exercise about how a phishing attack works. The idea behind phishing is to build a fake login page that looks like a real one, so the user believes it is genuine and enters their email and password. A small PHP script saves whatever they submit, and then the page redirects them to the real website, so they notice nothing. I carried the whole thing out on my own computer, using a test database and fake data, so no real person was affected and nothing illegal was done. The aim is to understand how the attack works in order to recognize it and defend against it. The screenshots below show the main steps rather than every single one.

---

## 2. Objective

Build a fake login page in a controlled local environment and show how it can capture a user’s credentials. The steps are: clone the public Bootstrap “signin” example page to make a fake login form that looks identical, write a PHP script that stores the email and password the user submits in a MySQL database, redirect the user to the real website afterwards so the deception goes unnoticed, and explain how a fake page like this would be delivered to people in practice. I cloned the public example page rather than a real company’s site so the exercise stays legal.

---

## 3. Environment

Everything runs on a single Windows computer using XAMPP, which provides the web server and the database. The server and the database run only on my computer.

| Tool | Role in the exercise |
| :--- | :--- |
| **XAMPP (Apache)** | Local web server that runs the fake page and the PHP script |
| **XAMPP (MySQL)** | Database that stores the captured email and password |
| **phpMyAdmin** | Web interface for creating the database, table and user, and checking the captured data |
| **Notepad++** | Editor used to write the `.html` and `.php` files |
| **Bootstrap 4 "signin" template** | Public example page cloned to build the fake one |
| **Working folder** | `C:\xampp-\htdocs\bootstrap` (holds the `.html` and `.php` files) |

---

## 4. Work Performed

### 4.1 XAMPP Setup and Database Preparation
I downloaded and installed XAMPP from apachefriends.org and started the Apache and MySQL modules in the XAMPP Control Panel. The Admin button on Apache opens localhost, and the Admin button on MySQL opens phpMyAdmin. In phpMyAdmin I created a database called bootstrap and, inside it, a table called usuario with two columns, mail and pass, to hold the captured email and password. Then, under the Privileges tab, I created a MySQL user called whitehat so the PHP script can connect to the database. The whitehat / whitehat2 password is deliberately weak because this is only a local practice; on a real site you would use a strong, unique password.

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Phishing_and_Social_Engineering_Analysis_Project/main/Figure%201.PNG" alt="Figure 1" width="100%">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Phishing_and_Social_Engineering_Analysis_Project/main/Figure%202.PNG" alt="Figure 2" width="100%">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Phishing_and_Social_Engineering_Analysis_Project/main/Figure%203.PNG" alt="Figure 3" width="100%">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Phishing_and_Social_Engineering_Analysis_Project/main/Figure%204.PNG" alt="Figure 4" width="100%">
</p>

### 4.2 Cloning the Legitimate Login Page
I opened the real Bootstrap “signin” page, right-clicked and chose “View page source”, and copied the code. Then I pasted it into Notepad++, tidied the formatting, and saved it as bootstrapsignin.html in the C:\xampp- \htdocs\bootstrap folder, so Apache serves it at http://localhost/bootstrap/bootstrapsignin.html. The one important change is in the form: I set its action to server.php, so that when the user clicks “Sign in” the email and password are sent to my PHP script instead of to the real login. The fake page looks identical to the original.

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Phishing_and_Social_Engineering_Analysis_Project/main/Figure%205.PNG" alt="Figure 5" width="100%">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Phishing_and_Social_Engineering_Analysis_Project/main/Figure%206.PNG" alt="Figure 6" width="100%">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Phishing_and_Social_Engineering_Analysis_Project/main/Figure%206.PNG" alt="Figure 6" width="100%">
</p>


