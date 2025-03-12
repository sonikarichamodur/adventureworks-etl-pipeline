# AdventureWorks Data Warehouse ETL Pipeline 

## 📌 Project Overview  
This project implements an **end-to-end ETL pipeline** that extracts, transforms, and loads data from multiple sources into a **star schema data warehouse** for the **AdventureWorks** dataset. The data is sourced from **MySQL, MongoDB, and a CSV file**, processed in **Python (Pandas, SQLAlchemy, PyMongo)**, and then stored in a structured format for optimized querying and analysis.

## 📂 Data Sources  
- **MySQL Database** (AdventureWorks)  
  - Extracted **Product** and **Date** dimensions  
  - Queried and exported **Vendor** data to a CSV file  
  - Queried **Employee** data and exported it as a JSON file for MongoD
- **MongoDB Collection** (Employee Dimension)  
- **CSV File** (Vendor Dimension)  

After conducting ETL processes to create the Product, Employee, and Vendor dimension tables and upload them to the AdventureWorks
Data Warehouse, a final ETL process brings everything together by constructing a Purchase Orders fact table, which links to these dimensions through foreign key relationships. This completes the star schema and enables structured, efficient analysis of purchase order data.

## 🛠️ ETL Process Summary

### **1️⃣ Extract Phase**
- Extracted data from **MySQL** for the **Product**, **Date**, and **Vendor** dimensions.  
- Queried **Employee** data from MySQL and exported it as a **JSON file**, then loaded it into **MongoDB**.  
- Queried **Vendor** data from MySQL and exported it as a **CSV file** for local storage.  
- Extracted **Purchase Orders** by merging **PurchaseOrderDetails** and **PurchaseOrderHeader**.

### **2️⃣ Transform Phase**
- Looked up primary keys from **Product, Employee, Vendor, and Date** dimensions to establish relationships.  
- Renamed, reordered, and dropped unnecessary columns to maintain a structured data model.  
- Standardized column formats (ex: converting byte columns to integers and ensuring date columns are datetime objects)  

### **3️⃣ Load Phase**
- Loaded the transformed **Product** and **Date** dimensions into the **MySQL Data Warehouse**.  
- Imported the **Employee JSON file** into **MongoDB** and extracted it back for integration.  
- Loaded the **Vendor CSV file** into the data warehouse after transformations.  
- Inserted the **Fact Table (fact_purchaseorders)** into the data warehouse, ensuring foreign key relationships with dimension tables.

## 📊 Data Validation  
To confirm the successful creation of the **AdventureWorks Data Warehouse**, a query aggregates **purchase order data** by **Vendor and Product**, calculating total quantities, unit prices, and line totals. 

## 🖥️ Technologies Used  
- **Python** (Pandas, SQLAlchemy, PyMongo)  
- **MySQL** (Relational Data Storage)  
- **MongoDB** (NoSQL Data Storage)  
- **CSV Files** (Local File Integration) 

## 📎 Dependencies  
Ensure you have the following Python libraries installed:  

```bash
pip install pandas pymysql sqlalchemy pymongo certifi
```
## 📌 Running this project 
1. Clone this repository:
```bash
git clone https://github.com/yourusername/adventureworks-etl.git
cd adventureworks-etl
```
2. Run the SQL scripts to set up the database (`AdventureWorks_MySQL.sql`, `Lab_02c_Create_Populate_Dim_Date.sql`).
3. Execute the Jupyter Notebook step by step to complete the ETL process.