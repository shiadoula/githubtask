# githubtask

im doing it :)

# Docker



------

[The Docker Handbook – 2021 Edition (freecodecamp.org)](https://www.freecodecamp.org/news/the-docker-handbook/)

 

Docker checklist:

Check that your docker is running: 

In the bottom right of your screen you should have the icon of a white whale with dots, if there are no dots it means you need to start up docker

Checking if your container is running (in terminal/command prompt):

docker ps -al

Starting up your container:

docker start sql

 

 

**Docker:**

What is Docker: https://www.youtube.com/watch?v=JprTjTViaEA



# ERDs



------

**Notes:**

ERDs (goes into more detail): https://dev.to/helenanders26/entity-relationship-diagrams-explained-by-sonic-the-hedgehog-1m68

 

ERD of Northwind: https://www.zentut.com/wp-content/uploads/downloads/2013/06/Northwind-Sample-Database-Diagram.pdf

 



# Primary and Foreign Keys



------

| **Primary Key**                                       | **Foreign Key**                                              |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| Helps you to uniquely identify a record in the table. | It is a field in the table that is the primary key of another table. |
| Primary Key never accept null values.                 | A foreign key may accept multiple null values.               |
| You can have the single Primary key in a table.       | You can have multiple foreign keys in a table.               |

 



# DML, DDL, DCL & TCL



------

**DML**: Data Manipulation Language (edit table in structure)

- SELECT (Note: Some put this in a category of it's own)
- INSERT
- UPDATE
- DELETE

**DDL**: Data Definition Language (alter structure)

- CREATE
- ALTER
- DROP
- TRUNCATE

**DCL**: Data Control Language (full control admins rights)

- GRANT
- REVOKE

**TCL**: Transaction Control Language (version controls)

- COMMIT
- ROLLBACK
- SAVEPOINT



# Data types



------

**VARCHAR**

Adaptable to different lengths of characters. Records MAX size.

**CHARACTER or CHAR**

Data must be at a fixed length. Fixed amount of space used.

**INT**

Holds a whole number/integer value (see also bigint, smallint and tinyint) positive or negative.

**DATE or TIME or DATETIME**

Stores both date and time

**DECIMAL or NUMERIC**

Fixed Precision and scale (digits to right of decimal point) numbers.

**BINARY**

Use to store binary data such as an image or file.

**FLOAT**

Scientific use (very large numbers)

**BIT**

Equivalent to binary (0,1 or NULL)



# CREATE database



------

```
CREATE DATABASE my_db
```



# CREATE table



------

```
CREATE TABLE film_table

(

FilmID INT IDENTITY (1,1) PRIMARY KEY NOT NULL

,Film_name VARCHAR (10) NOT NULL

,Film_type VARCHAR (6)

,Date_of_release date

,Director VARCHAR (30)

,Writer VARCHAR (30)

,Star VARCHAR (30)

,Film_language VARCHAR (3) NOT NULL

,Official_website VARCHAR (MAX)

,Plot_summary VARCHAR (MAX)

);
```



# ALTER Table



------

*Can be used to RENAME, MODIFY, ADD or DROP columns*

*It is better to change the CREATE TABLE statement and save this for future use*

```
ALTER TABLE film_table
ADD
rating DEC(2,1)
,Age_rating INT;
```



# INSERT INTO



------

Ensure that values are the same data type as the column you intend to insert them into.

**Example:**

```
INSERT INTO film_table

(

film_name,

film_type,

Date_of_release,

Director,

Writer,

Star,

Film_language,

Official_website,

Plot_summary

)



VALUES

('300',

'Action',

'2006-03-09',

'Zack Snyder',

'Mark Canton',

'Gerard Butler',

'ENG',

'www.spartaglobal.com',

'In 480 B.C. a state of war exists between Persia, led by King Xerxes (Rodrigo Santoro), and Greece. At the Battle of Thermopylae, Leonidas (Gerard Butler), king of the Greek city state of Sparta, leads his badly outnumbered warriors against the massive Persian army. Though certain death awaits the Spartans, their sacrifice inspires all of Greece to unite against their common enemy.'

),

('GoodFellas',

'Action',

'1990-09-09',

'Martin Scorsese',

'Nicholas Pileggi',

'Robert DeNiro',

'ENG',

'www.GoodFellas.com',

'A young man grows up in the mob and works very hard to advance himself through the ranks. He enjoys his life of money and luxury, but is oblivious to the horror that he causes. A drug addiction and a few mistakes ultimately unravel his climb to the top'

);
```



# CHECK function



------

To use the check function you state the column that you want to be constrained for example

```
CREATE TABLE Spartan(
Age int CHECK (Age >= 18)
)
```

This function would have it so that the column age cannot be set below 18



# Nomalisation



------

Database normalisation is the process of structuring a relational database in accordance with a series of so-called normal forms in order to reduce data redundancy and improve data integrity.

Video explaining normalisation: https://www.youtube.com/watch?v=UrYLYV7WSHM

**1st normal form:**

A database is in First Normal Form when the following conditions are satisfied:

Make everything Atomic

- - Data must be presented as small as it can be.
- There should be no repeating groups
  - For example, a table that records data on a book and its author(s) with the following columns: [Book ID], [Author 1], [Author 2], [Author 3] is not in 1NF because [Author 1], [Author 2], and [Author 3] are all repeating the same attribute

**2nd normal form:**

A database is in Second Normal Form when the following conditions are satisfied:

- It is in 1NF
- All non-key attributes are fully functional dependent on the primary Key

**3rd normal form:**

A database is in Third Normal Form when the following conditions are satisfied:

It is in 2NF

- There is no transitive functional dependency
  - i.e. A Transitive Functional Dependency is when a non-key column is Functionally Dependent on another non-key column, which is Functionally Dependent on the Primary Key.

 

 

![img](https://uksouth1-mediap.svc.ms/transform/thumbnail?provider=spo&inputFormat=png&cs=MWZlYzhlNzgtYmNlNC00YWFmLWFiMWItNTQ1MWNjMzg3MjY0fFNQTw&docid=https%3A%2F%2Ftestingcircle%2Esharepoint%2Ecom%2F%5Fapi%2Fv2%2E0%2Fdrives%2Fb%21ZnaJl9eq9UCyde9xSxqwlcwgr5EgYHlCir8OvEjplEgKdEhs2Q%5FRQo8vvGjwsbNZ%2Fitems%2F01R7TRNYCE3CBSHFRDYVGK2VMIJBLQKULF%3Ftempauth%3DeyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0%2EeyJhdWQiOiIwMDAwMDAwMy0wMDAwLTBmZjEtY2UwMC0wMDAwMDAwMDAwMDAvdGVzdGluZ2NpcmNsZS5zaGFyZXBvaW50LmNvbUBmZjE1YzY3Yy0yODcwLTRlOWYtYWRjMS03ZDYxZDg1NWI2NjciLCJpc3MiOiIwMDAwMDAwMy0wMDAwLTBmZjEtY2UwMC0wMDAwMDAwMDAwMDAiLCJuYmYiOiIxNjE1NTYxMjAwIiwiZXhwIjoiMTYxNTU4MjgwMCIsImVuZHBvaW50dXJsIjoiRUxxSUZGTjlHTEZFaCtpS3lrdmN6bXByWlZLRWs2eW9zdk1GVHFJN1hldz0iLCJlbmRwb2ludHVybExlbmd0aCI6IjE2MSIsImlzbG9vcGJhY2siOiJUcnVlIiwidmVyIjoiaGFzaGVkcHJvb2Z0b2tlbiIsInNpdGVpZCI6Ik9UYzRPVGMyTmpZdFlXRmtOeTAwTUdZMUxXSXlOelV0WldZM01UUmlNV0ZpTURrMSIsImFwcF9kaXNwbGF5bmFtZSI6Ik1pY3Jvc29mdCBUZWFtcyIsImdpdmVuX25hbWUiOiJTaGVocnlhYXIiLCJmYW1pbHlfbmFtZSI6IkRvdWxhdHphaSIsImFjIjoibHxtfGgiLCJhcHBpZCI6IjFmZWM4ZTc4LWJjZTQtNGFhZi1hYjFiLTU0NTFjYzM4NzI2NCIsInRpZCI6ImZmMTVjNjdjLTI4NzAtNGU5Zi1hZGMxLTdkNjFkODU1YjY2NyIsInVwbiI6InNkb3VsYXR6YWlAc3BhcnRhZ2xvYmFsLmNvbSIsInB1aWQiOiIxMDAzMjAwMTE1Q0U5NDIzIiwiY2FjaGVrZXkiOiIwaC5mfG1lbWJlcnNoaXB8MTAwMzIwMDExNWNlOTQyM0BsaXZlLmNvbSIsInNjcCI6Im15ZmlsZXMud3JpdGUgYWxsc2l0ZXMuZnVsbGNvbnRyb2wgYWxsc2l0ZXMubWFuYWdlIGFsbHByb2ZpbGVzLndyaXRlIiwidHQiOiIyIiwidXNlUGVyc2lzdGVudENvb2tpZSI6bnVsbH0%2EMk5rOVNHdVpoSjZGOUFCZlZsRE9ETUZOdU9ZM2tia05WcjFSdy9pSU1JMD0%26version%3DPublished&width=800&height=800&cb=63749593610)

 

 



# Creating a customer database



------

**Creating two tables in a DB:**

```
CREATE TABLE Customer
(
 CustomerID INT IDENTITY (1,1) PRIMARY KEY NOT NULL
 ,Name VARCHAR(255) NOT NULL
 ,height DECIMAL(7,3)
 ,is_happy BIT
);
CREATE TABLE Orders
(
  OrderID INT IDENTITY (1,1) PRIMARY KEY NOT NULL
  ,OrderNumber int NOT NULL
  ,CustomerID int
  ,FOREIGN KEY (CustomerID) REFERENCES Customer (CustomerID)
);
```

**Inserting data into the database:**

```
INSERT INTO Customer (Name, Height, is_happy)
VALUES
('Nishant Mandal', 185.5, 1)
,('Lee Boot', 187.5, 1)

 

INSERT INTO Orders (OrderNumber,CustomerID)
VALUES
(0033, 1)
,(0034, 2)
```



# Create a video games database



------

Create Tables:

```
CREATE TABLE Video_games
(
VideoGameName VARCHAR(30)
,Rating INTEGER
)
CREATE TABLE Video_game_developer
(
DeveloperName VARCHAR(30)
,HQ VARCHAR (20)
)
```

Adding Primary Key column:

```
ALTER TABLE video_games
ADD VideoGameID INT IDENTITY (1,1) PRIMARY KEY NOT NULL;

 

ALTER TABLE video_game_developer
ADD DeveloperID INT IDENTITY (1,1) PRIMARY KEY NOT NULL;
```

Adding Foreign Key column:

```
ALTER TABLE video_games
ADD DeveloperID INT
,FOREIGN KEY (DeveloperID) REFERENCES Video_game_developer(DeveloperID);
```

Inserting Data:

```
INSERT INTO Video_games 
(
 VideoGameName
 ,Rating
 )

VALUES 
('Super Mario Kart',3 )
,('The Legend of Zelda', 12)55
,('Sonic the Hedgehog', 3)

INSERT INTO Video_game_developer 
(
 DeveloperName
 ,HQ
)

VALUES 
('Nintendo', 'Japan')
,('Sega', 'Japan');
```

Querying Database:

```
SELECT VideoGameName, DeveloperName
FROM Video_games g
JOIN Video_game_developer d
ON g.DeveloperID =d.DeveloperID;
```



# SQL Statement Breakdown



------

![img](blob:https://teams.microsoft.com/f04f4e03-c53e-42f1-b698-2d7622ce6339)

 

![img](blob:https://teams.microsoft.com/dc5970b8-8894-4c59-b62b-e2b6ffda2948)

 

 

 



# Introduction to Querying



------



---Employees from London
SELECT * FROM Employees WHERE City = 'London'
​
----Number of products that are not discontinued
SELECT COUNT(*) FROM Products WHERE discontinued=1;
​
----Dealing with apostrophes
SELECT * FROM Suppliers WHERE Address = '29 King''s Way'
​
----Limit columns
SELECT CompanyName, City, Country, Region
FROM Customers
​
----Alphabetical ordering
SELECT CompanyName, ContactName
FROM Customers WHERE Country = 'France'
ORDER BY CompanyName ASC --DESC;

 



# WITH TIES



------

WITH TIES allows you to return more rows with values that match the last row in the limited result set.

Note that WITH TIES may cause more rows to be returned than you specify in the expression.

**Example:**

```
SELECT TOP 1 WITH TIES *, FROM [Order Details]
ORDER BY Quantity DESC
```



# CREATE VIEW



------

We can also use VIEWs

You need to have a goal in mind when creating a view. There are a number of scenarios where you will want to look for a view as a solution.

To hide the complexity of the underlying database schema, or customise the data and schema for a set of users.

To control access to rows and columns of data.

To aggregate data for performance.

```
CREATE VIEW French_Customers AS
SELECT CompanyName, ContactName, Phone
FROM Customers
WHERE Country = ‘France’
```



# Wild Cards



------

| %           | A substitute for zero or more characters                     |
| :---------- | :----------------------------------------------------------- |
| _           | A substitute for a single character                          |
| [charlist]  | Sets and ranges of characters to matchi.e. LIKE [ABC]%This will bring back anything starting with any of those letters. |
| [^charlist] | Sets and ranges of characters that don’t matchi.e. LIKE [^ABC]%This will bring back anything that does not start with those letters. |

Wildcards can be used as a substitute for any other characters in a string when using the LIKE operator

**Example 1 (returns product names which start with 'Ch'):**

```
SELECT *
FROM Products WHERE ProductName LIKE 'Ch%’;
```

**Example 2 (returns product names which begin with a vowel):**

```
SELECT *
FROM Products WHERE ProductName LIKE '[AEIOU]%’;
```



# Concatenation



------

Concatenate using + along with single quotes

Alias (rename) column using AS (optional) and double quotes (if more than one word) to change column headers

**Example:**

```
Select FirstName+' '+LastName as 'Full Name'
FROM Employees
```



# Arithmetic Operators



------

| +    | Add (can be used on DATETIME columns)                        |
| :--- | :----------------------------------------------------------- |
| -    | Subtract (can be used on DATETIME columns)                   |
| *    | Multiply                                                     |
| /    | Divide                                                       |
| %    | Percentage (Modulo)Returns the integer remainder of a division. For example, 12 % 5 = 2 because the remainder of 12 divided by 5 is 2. |

**Example:**

```
SELECT UnitPrice, Quantity, Discount,  
UnitPrice * Quantity * (1-Discount) AS “Net Total”
FROM [Order Details];
```



# ORDER BY



------

Note the use of the Column Alias in the ORDER BY clause.

This could also have been written:

```
ORDER BY UnitPrice * Quantity DESC
```

Or

```
ORDER BY 4 DESC
```

Use of numbers is not best practice (main use is with UNION see later)

DESC is short for DESCENDING

ASC is the default (ASCENDING)

**Example:**

```
SELECT UnitPrice, Quantity, Discount, UnitPrice * Quantity AS ‘Gross Total’

FROM [Order Details]

ORDER BY ‘Gross Total’ DESC
```



# String Functions



------

| SUBSTRING      | SUBSTRING(expression, start, length)SUBSTRING(name,1,1) for the initial |
| :------------- | :----------------------------------------------------------- |
| CHARINDEX      | CHARINDEX(‘a’, ’text’) to search for a string e.g. find ‘a’ in a column called ‘text’ |
| LEFT or RIGHT  | LEFT(name,5) for the first (or last) 5 characters            |
| LTRIM or RTRIM | Used to remove spaces at the beginning or end of a string.   |
| LEN            | LEN(name) for the length of the name                         |
| REPLACE        | REPLACE(name,’ ’,’_’) to replace spaces with underscores     |
| UPPER or LOWER | UPPER(name) to convert to all upper (or lower) case.         |

**Examples:**

--==SUBSTRING(expression, start, length)==

```
SELECT SUBSTRING('Nish',2,2);

--Returns: 'Ni'
```

*--==CHARINDEX==*

```
SELECT CHARINDEX('i', 'Nishant');

--Returns: '2'
```

*--==LEFT or RIGHT==*

```
SELECT LEFT('Sparta Global', 6);

--Returns: 'Sparta'
SELECT RIGHT('Sparta Global', 6);

--Returns: 'Global'
```

*--==LEN==*

```
SELECT LEN('Hannah');

--Returns: '6'
```

*--==REPLACE==*

```
SELECT REPLACE ('Nish', 'i', 'a');

--Returns: 'Nash'
```

*==UPPER or LOWER==*

```
 SELECT UPPER ('nish')
--Returns 'NISH'

SELECT LOWER ('NISH')

--Returns: 'nish'
```



# DATETIME Functions



------

| GETDATE     | SELECT GETDATE() to return the current date and time         |
| :---------- | :----------------------------------------------------------- |
| SYSDATETIME | `SELECT SYSDATETIME()` to return the date and time of the computer being used |
| DATEADD     | `DATEADD(dd,5,OrderDate) AS “Due Date”` to add 5 days        |
| DATEDIFF    | `DATEDIFF(dd,OrderDate,ShippedDate) AS “Ship Time`” to calculate difference between dates |
| YEAR        | `SELECT YEAR(OrderDate) AS “Order Year”` to extract the year from a date. |
| MONTH       | `SELECT MONTH(OrderDate) AS “Order Month”` to extract the year from a date. |
| DAY         | `SELECT DAY(OrderDate) AS “Order Day” `to extract the day from a date. |

**Examples:**

```
SELECT GETDATE();
SELECT SYSDATETIME();

 

SELECT OrderDate
,DATEADD(yyyy,5,OrderDate) AS '5 years after Order Date'
FROM Orders

 

SELECT OrderDate, ShippedDate
,DATEDIFF(dd, OrderDate,ShippedDate) AS 'Shipping Time'
FROM Orders

 

SELECT YEAR(OrderDate) 
AS 'Shipping Time'
FROM Orders;

 

SELECT OrderDate, ShippedDate
,DATEDIFF(dd, OrderDate,ShippedDate) AS 'Shipping Time'
FROM Orders

 


SELECT FirstName +' ' + LastName AS 'Name'
, FORMAT(BirthDate, 'dd/MM/yyyy') AS 'Birth Date'
, CAST (BirthDate AS DATE) AS 'Date of Birth'
, DATEDIFF (yyyy, BirthDate, GETDATE())AS 'Age'
, DATEDIFF (dd, BirthDate, GETDATE())/365.25 AS 'Age'
FROM Employees;
```



# SELECT CASE



------

**Example below. Also Highlights different formats:**

```
SELECT FirstName + ' ' + LastName AS 'Employee Name',
--Unformatted Age
DATEDIFF(dd,BirthDate,GETDATE())/365.25 AS 'Age',
--Using Floor function (just removes the everything after the Decimal)
FLOOR(DATEDIFF(dd,BirthDate,GETDATE())/365.25) AS 'Age Floor',
--Round to 2 DP
ROUND((DATEDIFF(dd,BirthDate,GETDATE())/365.25),2) AS 'Age Round',
--CAST to INT
CAST((ROUND((DATEDIFF(dd,BirthDate,GETDATE())/365.25),0)) AS INT) AS 'Age Round with CAST',
CASE WHEN (DATEDIFF(DD,BirthDate,GETDATE())/365.25)>=65 THEN 'Retired'
WHEN (DATEDIFF(DD,BirthDate,GETDATE())/365.25)>=60 THEN 'Retirement Due'       
ELSE 'More than Five Years to Go'
END AS 'Retirement Status'
FROM Employees;
```



# SELECT CASE using VIEWS



------

```
CREATE view EmployeeAge AS
SELECT
    EmployeeID,
    FirstName,
    LastName,
    floor(datediff(dd, BirthDate, getdate()) / 365.25) as 'Age'
FROM Employees;
```

 

```
SELECT
    FirstName + ' ' + LastName as 'Name',
    Age,
    CASE
        when Age >= 65 then 'Retired'
        when Age >= 60 then 'Retirement Due'
        else 'More than five years to go'
    END
    AS 'Retirement Status'
FROM EmployeeAge;
```

 

##  



# Aggregate Functions



------

| SUM   | SUM(OrderTotal) for the grand total of a column for all rows selected |
| :---- | :----------------------------------------------------------- |
| AVG   | AVG(UnitPrice) for the average of a column for all rows selected |
| MIN   | MIN(UnitPrice) for the smallest value in a column for all rows selected |
| MAX   | MAX(UnitPrice) for the largest value in a column for all rows selected |
| COUNT | COUNT(*) for the number of NOT NULL rows selected. If * is used then all rows are counted. |

**Example:**

 

```
SELECT
SupplierID
SUM(UnitsOnOrder) AS 'Total on Order'
,AVG(UnitsOnOrder) AS 'Average on Order'
,MIN(UnitsonOrder) AS 'Min on Order'
,MAX(UnitsOnOrder) AS 'Max on Order'
FROM Products
GROUP BY SupplierID;
```

 

**(NOTE: If you use an aggregate function in a SELECT statement, all other columns must either be an aggregate or in the GROUP BY clause)**



# HAVING Statements



------

HAVING is used instead of WHERE when filtering on subtotals/grouped data

Column Aliases cannot be used in the HAVING clause

Aggregate functions are not available for use in the WHERE clause due to the SQL processing sequence

 

**Example 1:**

```
SELECT SupplierID,
SUM(UnitsOnOrder) AS “Total On Order”,
AVG(UnitsOnOrder) AS “Avg On Order”
FROM Products
GROUP BY SupplierID
HAVING AVG(UnitsOnOrder)>5
```

 

**Example 2:**

```
SELECT et.EmployeeID 
,e.FirstName
,e.LastName
,COUNT(TerritoryID) 
AS 'Number of territories covered'
FROM EmployeeTerritories et
INNER JOIN Employees e 
ON et.EmployeeID = e.EmployeeID
GROUP BY et.EmployeeID
,e.FirstName
,e.LastName
HAVING COUNT(TerritoryID) > 5
```

 



# Joins



------

![img](blob:https://teams.microsoft.com/9c876799-7872-46a0-8538-a059d9d94ce4)

 

**Example 1:**

```
SELECT ProductName, UnitPrice, CompanyName AS 'Supplier', 
        CategoryName AS 'Category'
FROM Products p 
INNER JOIN Suppliers s ON p.SupplierID = s.SupplierID
INNER JOIN Categories c ON p.CategoryID = c.CategoryID

```

**Example 2 (with aggregates):**

```
SELECT p.SupplierID As 'Supplier ID', CompanyName AS 'Company Name', AVG(p.UnitsOnOrder) AS 'Average On Order'
FROM Products p
INNER JOIN Suppliers s ON p.SupplierID = s.SupplierID
GROUP BY p.SupplierID, CompanyName
```

 

**Example 3 (with formatting)**

```
SELECT FORMAT(o.OrderDate,'dd/MM/yyyy') as'Order Date',
FORMAT((od.UnitPrice*od.Quantity)*(1-od.Discount),'C', 'en-US') AS 'Net total',
c.CompanyName
FROM Orders o
INNER JOIN [Order Details] od ON o.OrderID=od.OrderID
INNER JOIN Customers c ON C.customerID=o.CustomerID
WHERE(od.UnitPrice*od.Quantity)*(1-od.Discount)>100

```



# Subqueries



------

A subquery may occur in any of the following clauses:

```
SELECT (nested subquery – returns single value only)
FROM (inline view)
WHERE (nested subquery)
```

 

**Example 1 (subquery in SELECT clause- also, aggregate with inner Join):**

```
SELECT OrderID, ProductID, UnitPrice, Quantity, Discount,
  (SELECT AVG(UnitPrice) FROM [Order Details] od) AS 'Avg Price'
FROM [Order Details]
```

 

**Example 2 (subquery in FROM clause. Note - subquery acting like a table):**

 

```
SELECT *
   FROM [Order Details] od
   INNER JOIN 
     (SELECT ProductID, SUM(UnitPrice*Quantity) AS totalamt
     FROM [Order Details]
     GROUP BY ProductID) sq1 ON sq1.ProductID=od.ProductID

 
```

 

**Example 3 (subquery in WHERE clause):**

```
SELECT OrderID,
   ProductID,
   UnitPrice,
   Quantity,
   Discount
FROM [Order Details]
WHERE ProductID IN (SELECT ProductID FROM Products WHERE Discontinued='1');
```

 

**Example 4**

```
SELECT
    emp.EmployeeID,
    emp.Name,
    emp.Age,
    CASE
        when emp.Age >= 65 then 'Retired'
        when emp.Age >= 60 then 'Retirement Due'
        else 'More than five years to go'
    END
    AS 'Retirement Status'
FROM
(
    SELECT
        EmployeeID,
        FirstName + ' ' + LastName as 'Name',
        floor(datediff(dd, BirthDate, GetDate()) / 365.25) as 'Age'
    FROM Employees
) emp;
```



# UNION

 

------

Below is a contrived example, showing how you could list all Employee IDs in the same column as all Supplier IDs

 

UNION ALL returns 38 rows

 

UNION removes any duplicates and returns 29 rows

 

Both SELECT statements must have the same number of columns in the SELECT clause (same type)

 

Only the Column Alias in the first SELECT will be applied

 

ORDER BY 1 may be more appropriate if column names differ

 

SELECT EmployeeID AS ‘Employee/Supplier’
FROM Employees
UNION ALL
SELECT SupplierID 
FROM Suppliers