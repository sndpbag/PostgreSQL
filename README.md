

## ১. PostgreSQL কী?

PostgreSQL হলো একটি **open-source relational database management system (RDBMS)**। এটি বিশ্বের সবচেয়ে advanced এবং শক্তিশালী database systems এর মধ্যে একটি। PostgreSQL-কে প্রায়ই "Postgres" নামেও ডাকা হয়।

**মূল বৈশিষ্ট্য:**
- সম্পূর্ণ বিনামূল্যে ব্যবহার করা যায়
- ACID compliance (Atomicity, Consistency, Isolation, Durability)
- Complex queries এবং advanced features support করে
- JSON, XML, Arrays এর মতো modern data types support করে
- High performance এবং scalability প্রদান করে

## ২. PostgreSQL-এ Database Schema-র উদ্দেশ্য কী?

**Database Schema** হলো database-এর একটি logical structure বা blueprint যা define করে:

- **Tables কীভাবে organize হবে**
- **Data কীভাবে store হবে**
- **Tables এর মধ্যে relationship কী হবে**
- **Data types এবং constraints কী থাকবে**

**Schema-র সুবিধা:**
- Database-এর structure organized রাখে
- Data integrity maintain করে
- Security এবং access control প্রদান করে
- একাধিক user এর জন্য namespace তৈরি করে

## ৩. Primary Key এবং Foreign Key ব্যাখ্যা

### **Primary Key:**
- একটি table-এর প্রতিটি row-কে **uniquely identify** করে
- **Null value হতে পারে না**
- একটি table-এ শুধুমাত্র **একটি Primary Key** থাকতে পারে
- Automatically index তৈরি হয়

**উদাহরণ:**

CREATE TABLE students (
    student_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);


### **Foreign Key:**
- অন্য table-এর Primary Key-র reference করে
- **Tables এর মধ্যে relationship** তৈরি করে
- **Referential integrity** maintain করে
- একটি table-এ **একাধিক Foreign Key** থাকতে পারে

**উদাহরণ:**

CREATE TABLE enrollments (
    enrollment_id SERIAL PRIMARY KEY,
    student_id INTEGER REFERENCES students(student_id),
    course_name VARCHAR(100)
);


## ৪. VARCHAR এবং CHAR Data Types এর পার্থক্য

### **VARCHAR (Variable Character):**
- **Variable length** string store করে
- Actual data যতটুকু জায়গা নেয় ততটুকুই use করে
- **Memory efficient**
- Maximum length specify করতে হয় (যেমন: VARCHAR(100))

### **CHAR (Character):**
- **Fixed length** string store করে
- সবসময় specified length-এর সমান জায়গা নেয়
- Shorter string হলে **space দিয়ে pad** করে
- **Fast processing** কিন্তু memory বেশি ব্যবহার করে

**উদাহরণ:**

-- VARCHAR example
name VARCHAR(50)  -- "sndp" শুধু 4 character জায়গা নেবে

-- CHAR example  
gender CHAR(1)    -- "M" বা "F" সবসময় 1 character জায়গা নেবে


## ৫. SELECT Statement-এ WHERE Clause-এর উদ্দেশ্য

**WHERE clause** ব্যবহার করা হয় database থেকে **specific data filter** করার জন্য। এটি condition specify করে যে কোন rows return করা হবে।

**মূল কাজ:**
- **Data filtering:** শুধুমাত্র নির্দিষ্ট condition মেনে চলা rows দেখায়
- **Performance improvement:** অপ্রয়োজনীয় data retrieve করা থেকে বিরত রাখে
- **Precise results:** Exact যে data দরকার সেটাই আনে

**উদাহরণ:**

-- সব students দেখানো
SELECT * FROM students;

-- শুধু 18 বছরের বেশি students দেখানো  
SELECT * FROM students WHERE age > 18;

-- নির্দিষ্ট নামের student খোঁজা
SELECT * FROM students WHERE name = 'sandipan';

-- একাধিক condition
SELECT * FROM students 
WHERE age >= 18 AND city = 'kolkata';


**WHERE clause ছাড়া:** Table-এর সব data return হবে । 
**WHERE clause সহ:** শুধু condition match করা data return হবে । 

 