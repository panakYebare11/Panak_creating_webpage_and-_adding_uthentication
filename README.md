====SESSION 1======
steps for spring project
first i have downloaded the spring project file from start.spring.io by selecting 
project       : Gradle - Groovy
Language      : Java
Spring Boot   : 3.5.0
Project Metadata
Group
com.example
Artifact
StudentDetails
Name
StudentDetails
Description
Demo project for Spring Boot
Package name
com.example.StudentDetails
Packaging
Jar
Java
17
Dependencies 
Spring web for spring libraries
spring Dev tools which autmatically starts for every save action
then Generate the file and extract it in Desktop
import the file in Eclipse
This section finishes the creation and import of project in Eclipse 
========SESSION 2========= 
Here we need to connect our data base to spring application
in spring we will use ORM concept to link DB and application
here i have used H2 Database 
for using H2 as database we need to add implementation in dependencies section and runTimeOnly in build.gradle
implementation 'org.springframework.boot:spring-boot-starter-data-jpa'  and runTimeOnly 'com.H2database:h2' by saving you see external libraries have been added to the packag and Dependencies module in project  structure
create a new package in root directory by name Repository 
note Repository means which is used for defining the folders related to Database
create a class in Repository package named student
declare varibles and crete constructors and getters and setters
add these two line in application.properties for letting know your application is using H2 database
spring.datasouce.url=jdbc:h2:mem:testdb
spring.jpa.show-sql=true
also add these lines so that you can see the databse console in /h2-console
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
then create a innterface in repository package by nme StudentRepository and extend by CrudRepository
then you inject the student repository object in main application 
you can add the rows by object_name.(new classname(parameters those are defined in constructor))
Then create Controller packge in root package aand creaet a new Class in Controller package by name StudentController.java
then next step is securing our backend add these lines in build.gradle
testImplementation 'org.springframework.security:spring-security-test'
implementation 'org.springframework.boot:spring-boot-starter-security'
so you wont get the h2-console by defult you need to add the security config file in root package
this is beacause Spring security will secure all endpoints present in the Project so we need to say externally to spring that this URL sould be excluded in security
here we use https methods to implement this
then i have created Service package where we can check the enter username and password is valid or not and additionally we have added the security config for customizing the security filter chain
like we have removed authoization for h2-console and added BCrypt Algorithm for encoding passwords.
# Panak_creating_webpage_and-_adding_uthentication
