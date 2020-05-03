# IIEC_RISE_DOCKER_COMPOSE_WEBSERVER_PROJECT

1) I am Using RedHat Linux 8 in this project. First of all install the docker

2) Then stop the firewall using the following command ```systemctl stop firewalld```

3) Now start the docker using the command ```systemctl start docker```

4) We need Images to proceed further so pull the following images  
   for mysql use ```docker pull mysql:5.6``` command,           
   for phpmyadmin use ```docker pull phpmyadmin/phpmyadmin``` and             
   for httpd use ```docker pull httpd```
   
   ![](Images/1.Starting%20docker%20and%20Pulling%20Images.jpg)

5) Next Step we need to configure Mysql. To Do that use the following command
               
    ```docker run -it -e MYSQL_ROOT_PASSWORD=(any password you like) -e MYSQL_USER=(any user name) -e MYSQL_PASSWORD=(any password) -e             MYSQL_DATABASE=(any database name) --name db mysql:5.6 ```
    
    After that you will get the following prompt which means connection success and you are good to go
    
    ![](Images/2.Mysql%20Connectio%20Success.jpg)
    
6) Now to check the connection and to know the IP of mysql run the commands ```docker inspect db | grep IP``` 
        and after this command we will get the ip so use the command ```mysql -h 172.17.0.2 -u sabari -predhat```
        
    ![](Images/3.mysql%20inspect%20IP.jpg)
    
7) Now we need to configure PHPMYADMIN to do that run the following command
     ```docker run -it -e PMA_PASSWORD=(password you gave for mysql user) -e PMA_USER=(mysql usernawe) -e PMA_HOST=(Hostname/HostIP of mysql) --name db mysql:5.6 ```
     
8) Now Its time for docker-compose before you do that you need to install docker-compose
    To install it and to know more about docker-compose Go to [https://docs.docker.com/compose/install/]()
    
9) Its time to compose so now run the command ```docker-compose up``` . Thats it your docker-compose and webserver is running

   ![](Images/5.docker-compose%20up.jpg)
   
   ![](Images/7.phpmyadmin%20success.jpg)
   
10) Once your job completes now its time to stop the compose by the following command ```docker-compose down```


   ![](Images/6.docker-compose%20down.jpg)
   
   
 Note : After doing docker-compose down its best to remove all containers using the command
         ```docker container rm -f $(docker ps -aq)``` so that we dont get any problems in future while doing docker-compose up
