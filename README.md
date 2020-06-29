# nodejs_mysql_demo
Simple backend/frontend code with MySQL and Node.JS

## Pre-reqs
2x Ubuntu 18.04 VMs, 1vCPU and 1GB RAM minimum

## Instructions:

### Backend
1. Install dependencies:
```
backend:~$ sudo apt update
backend:~$ sudo apt install mysql-server -y
```

2. Setup the database:
```
backend:~$ git clone https://github.com/rodrigocastrillon/nodejs_mysql_demo
backend:~$ cd nodejs_mysql_demo/backend
backend:~$ mysql -uroot < create_db.sql
backend:~$ mysql -uroot -e "GRANT ALL PRIVILEGES ON socka.* TO 'node'@'%' IDENTIFIED BY 'node';"
```

3. Configure MySQL Server:
```
backend:~$ sudo sed -i.bak '/bind-address/d' /etc/mysql/mysql.conf.d/mysqld.cnf
backend:~$ sudo service mysql restart
```


### Frontend
1. Install dependencies:  
```
frontend:~$ curl -sL https://deb.nodesource.com/setup_10.x -o nodesource_setup.sh
frontend:~$ sudo bash nodesource_setup.sh
frontend:~$ sudo apt update
frontend:~$ sudo apt install nodejs -y
```

2. Configure NPM:  
```
frontend:~$ npm init
(Hit 'Enter' for all prompts)
frontend:~$ npm install express express-fileupload body-parser mysql ejs req-flash --save
frontend:~$ sudo npm install nodemon -g
```

3. Get the code and run it:
```
frontend:~$ git clone https://github.com/rodrigocastrillon/nodejs_mysql_demo
frontend:~$ cd nodejs_mysql_demo/
frontend:~$ sudo node app.js <DB BACKEND IP>
```
*NOTE:* Use the 'sudo' command above or else Node will fail to use the HTTP port 80.  
You should then see:  
```
DB Server: X.X.X.X
Server running on port: 80
Connected to database
```
