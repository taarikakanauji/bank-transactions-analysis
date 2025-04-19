# Banking Transactions Analysis - Power BI Report 

![BI Report](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/BI-Report.jpg)

## Problem Statement

Stakeholders across various departments lack a centralized, data-driven view to effectively monitor and analyze banking transactions across different regions, transaction types, and fraud indicators. This gap makes it challenging to detect suspicious patterns, assess operational efficiency, and make informed decisions based on transaction success or failure rates. There is a need for an interactive dashboard that provides actionable insights.

This dashboard helps stakeholders track and analyze banking transactions based on region, transaction type, fraud status, and transaction outcomes (successful or failed). It delivers data-driven insights to uncover anomalies, enhance fraud detection, optimize operations, and improve service performance. The dashboard is designed for key stakeholders:

- Banking Executives & Risk Managers

- Fraud Detection & Compliance Teams

- Operations & Support Teams

- Regional Managers & Analysts

# Objective

- `Monitor Transaction Performance` by tracking key metrics, including total transactions, highest and lowest transaction amounts, and success rates.

- `Analyze and Compare Fraud Incidents` across different transaction types to identify high-risk areas and strengthen fraud prevention strategies.

- `Balance Regional Transaction Volume` by identifying regions with low activity and developing initiatives to improve engagement and service efficiency.

- `Enhance Performance of Underutilized Transaction Types` by pinpointing categories with low success rates or high failure rates, and implementing targeted improvements.

- `Identify Potential Risks and Recommend Actions` to improve transaction security, operational efficiency, and customer satisfaction

## Key Questions

    Q : How is the latency varying in all of the transactions?

    Q : What is the ratio of successful and failed transactions?

    Q : What are the overall banking transactions insights including total transactions and transaction amount?

    Q : Which geographic locations/states have the highest transactions and which need attention?

    Q : How are the transations distributed throughout the time of day?

    Q : What is total number of fraudulent transactions and its total amount?

    Q : How do transactions vary in terms of internet bandwidth group?

    Q : What type of devices are used in transactions and which types are leading and/or trailing?

    Q : Which regions are recording the highest number of transactions?

    Q : Which areas to focus on for impovements based on this data?

## Steps followed 

As a Business Analyst for a leading banking organization, I was tasked with developing an interactive report/dashboard to help stakeholders monitor transaction performance, fraud trends, and regional activity across the country. The goal was to provide actionable insights to enhance fraud detection, operational efficiency, and customer trust. Below, I explain my step-by-step approach to designing this dashboard in Power BI:

- Step 1 : Load data into Power BI Desktop. The dataset is a csv file.

- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.

- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".

- Step 4 : After a thorough review and cleanup, we now have a data which contains no errors or empty values across columns — indicating a high-quality dataset ready for transformation and visualization.

- Step 5 : In the report view, under the view tab, default theme was selected.

- Step 6 : Creating KPI Cards for Key Metrics - To provide stakeholders with a clear summary, I created four KPI cards displaying high-level performance indicators as shown below. These KPIs offer a real-time snapshot of operational health, and help in making data-driven decisions quickly and effectively.

        Total Transactions – Total no. of transactions.
        Measure Used : Total transactions  = DISTINCTCOUNT(‘bank_transaction_data’[Transaction ID])

        Success transactions – Successful transactions.
        Measure Used : Success transactions  = DIVIDE(CALCULATE(COUNT(‘bank_transaction_data’[Transaction Status]), 
        ‘bank_transaction_data’[Transaction Status] = “Success”), 
        COUNT (‘bank_transaction_data’[Transaction Status]))


        Failed transactions – Failed transactions.
        Measure Used : Failed transactions  = DIVIDE(CALCULATE(COUNT(‘bank_transaction_data’[Transaction Status]), 
        ‘bank_transaction_data’[Transaction Status] = “Failed”), 
        COUNT (‘bank_transaction_data’[Transaction Status]))


        Transaction amount – Total transaction amount.
        Measure Used : Transaction amount  = SUM(‘bank_transaction_data’[Transaction Amount])


   I formatted these cards with currency symbols and percentage representation to make trends easily understandable. These KPIs help executives quickly assess fundamental performance without diving into granular data.

   ![KPI](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/kpi.jpg)

- Step 7 : Visualizing transactions by Region with a Map - To show transactions geographically, I used a Azure map to showcase the total transactions count coming from various regions of the world.

        Fields used:

        Latitude and Longitude

        Size: Total Transactions
    

  This visual quickly highlights top-performing regions (e.g., Europe and America) and underperforming regions (e.g., the Central, Asia). The map helps regional managers focus efforts where they’re needed most and also keep strengthening the areas which are operating efficiently.

   ![Region Map](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/region%20map.jpg)

           
- Step 8 : Representing the number of transactions based on time of day (Transactions distribution by time) - I added a line chart to show transactions are happening during different times of the day. 

        Fields Used:

        X-axis: Time

        Y-Axis: Total Transactions

   The chart revealed that the trasactions reach their peak around 10:30am and 11:00am, indicating the high usage during morning time. This insight suggests prioritizing system uptime during that time.

  ![Timeline](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/time-%20line.jpg)

- Step 9 : Categorizing transactions based on latency range - To better understand how much time it takes for customers to do transactions, I created a bar chart. This chart helps analyze the latency ranges with their respective number of transactions, and indicates if the transactions are fast enough or slow.

        Fields used:

        Y-Axis: Total transactions

        X-axis: Latency Group

   This showed that majority of the transactions happening are within a suitable latency range and this ensures customers can finish their transactions with great speed.

- Step 10 : Type of device used shown by a bar chart - I used a simple bar chart to show what types of devices are used across all transactions and what is the number of transactions for each type. 

        Fields used:

        Y-Axis: Total Transactions

        X-Axis: Device Type

  The clear winner was Mobile in this case, followed by Desktop. This evidently shows the majority of the users are using Mobile devices to do their transactions. The IT team can use this information to further optimize the mobile app and introduce new features to capture and convert more audience from the Desktop category, into Mobile category.

![Latency - Device](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/latency%20-%20device.jpg)

- Step 11 : Fraud Flag or not with a pie chart - This pie chart is pretty simple, indicating the percentage division between transactions based on whether they were flagged as fraudulent or not. 

        Fields used:

        Legend: Fraud Flag (True or False)

        Values: Total Transactions

  The legit transactions were 48.1% while the rest were marked as fraudulent. This indicates a concerning statistic that the security and IT team can dive deep into, and improve the overall security of the transactions and authentication.   


- Step 12 : Transaction type categorical percentages using pie chart - This chart highlights the percentage distribution between the different types of transactions. 

     
        Fields used:

        Legend: Transaction Type (Transfer, Deposit or Withdrawal)

        Values: Total Transactions

   The maximum recorded transactions were of Withdrawal type, followed by Deposit and lastly Transfer. 

   ![Fraud Flag and Type](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/fraud%20flag%20and%20type.jpg)   


- Step 13 : Implementing filters in the dashboard - To enhance user experience in our report, I implemented a set of 4 slicers for the user to filter data based on their requirement. They are easily accessible on the dashboard, in the top section.

  Setting up slicers for interactive dynamic filtering - To ensure users could dynamically explore the data by interacing and filtering the entire report, I implemented slicers and these filters help in narrowing down the analysis to specific dimensions of interest.

  I added slicers for:

  Transaction Type (Transfer, Deposit or Withdrawal)

  Transaction Status (Failed or Success)

  Device Used (Desktop or Mobile)

  Network Slice ID (Slice1, Slice1 or Slice3)

  I chose dropdown-style slicers for a clean interface, ensuring they influence all report visuals. This allows business teams to filter data—for example, comparing the transaction frequencies in terms of various scenarios. 


- Step 14 : Implementing Reset Filters - To improve the usability and interactivity of the Power BI report, I included a Reset Filter icon that enables users to effortlessly clear all slicer selections and restore the report to its original default view. This helps eliminate the fear of applying filters by reassuring users they can easily revert any changes. ("What if I can't undo?").

  First, Using the Insert > Image option, I added a reset or refresh icon. This icon was placed near the filters for visibility and ease of access.

  Then I cleared all slicer selections (Transaction Type, Transaction Status, Device Used, and Network Slice ID). 

  I enabled Action on the reset filters icon by setting, Type- Bookmark and Bookmark- Clear all Filters. This ensures that when the icon is clicked, all slicers and filters return to their default (unselected) state.


- Step 15 : Implementing page navigators: To add additional coverage of crucial information, I implemented two additional page navigators namely: Fraud Detection and Transaction Details. 

  Both the pages are covered in the below topics.

# Fraud Detection Page


![BI Report Full 2](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/BI-Report-fraud.jpg)


To identify and analyze fraudulent transactions by examining patterns across transaction types, bandwidth groups, network slices, and regions, enabling proactive fraud mitigation

This page consists of different types of visual indicators related to fraudulent transactions. The page showcases a combination of KPIs, pie chart, bar chart and map to highlight a comprehensive view regarding fraudulent transactions.

- KPIs used

  `Fraudulent Transactions` - Showing total number of fraudulent transactions

  `Transaction Amount` - Shows the total amount in such transactions

  ![KPI Fraud](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/kpi-fraud.jpg)

- Transaction Status 
  
  This binary visual shows the number of transactions that were marked as failed or successful in the fraudulent category. As seen in the image below, a higher number of transactions were failed, which is a good indicator of how secure the system is, but there's further scope of improvement based on the number of successful transactions.

  ![Status Fraud](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/status-fraud.jpg)

- Bandwidth group and Network Slice 

  These two graphs the transactions categorization based on the bandwidth group and network slice ID respectively. 

  ![Band Network Fraud](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/band-network-Fraud.jpg)


  **Insights**

    (a)Total 481 Fraud Transactions found with around 379k amount

    (b)Fraud percentage is similar across Transfer, deposit, withdrawal types

    (c)High bandwidth is preferred in fraud transactions

  **Challenges**

    (a)Outdated security systems for fraud transaction

    (b)Lack of modern two factor authentication in devices

  **Recommendations**

    (a)Monitor high-bandwidth transactions and Enforce 2FA with biometrics for high-risk transactions.

    (b)Upgrade to AI-driven fraud detection for real-time anomaly spotting.


# Transaction Details Page

![BI Report Full 3](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/BI-Report-detail.jpg)

Analyze granular transaction data to detect fraud patterns in real-time, focusing on sender/receiver accounts, transaction types, bandwidth usage, and network slices.

This page will show a tabular view of the transactions, including fields such as Transaction ID, Sender Account ID, Receiver Account ID, Transaction Type and many more. This offers a more technical and detailed view of each transaction.

**Insights**

(a)150–250 Mbps Bandwidth Dominates Fraud

(b)Network Slice "Slice 2" as Fraud Hotspot

(c)Sender-Receiver Account Pairs (Recurring transfers between signal potential hidden fraud)

**Challenges**

(a)Overloaded Network Slices - "Slice 2" handles both legitimate and fraudulent traffic, making isolation difficult

(B)More traffic before 10.15am and around 11am can lead to more fraud transaction

**Recommendations**

(a)Isolate "Slice 2" for Security Audit- Partner with cybersecurity firms to scan for vulnerabilities

(b)Enforce Multi-Device Authentication

# Snapshot of Report (Power BI Service)

  ![Service Report Full](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/Service-Report-Full.jpg)
  

# Report Snapshot (Power BI DESKTOP)

  ![BI Report Full 1](https://github.com/taarikakanauji/bank-transactions-analysis/raw/main/images/BI-Report-Full-1.jpg)

# **Project Resources**  

### **Detailed Report (PDF)**  
[Insights of Banking Transactions (PDF)](https://github.com/taarikakanauji/bank-transactions-analysis/blob/main/Insights%20for%20Bank%20Transactions.pdf)


### **Power BI Desktop Demo**  
[Power BI Demo (MKV)](https://github.com/taarikakanauji/bank-transactions-analysis/blob/main/Power-BI-Demo.mkv)  

### **Power BI Service Demo**  
[Power BI Service Demo (MKV)](https://github.com/taarikakanauji/bank-transactions-analysis/blob/main/Power-Service-Demo.mkv)  

### **PBIP Files**  
- **Report:** [Report Files](https://github.com/taarikakanauji/bank-transactions-analysis/tree/main/Bank%20Transaction%20Report.Report)  
- **Semantic Model:** [Semantic Model Files](https://github.com/taarikakanauji/bank-transactions-analysis/tree/main/Bank%20Transaction%20Report.SemanticModel)  
- **Project File:** [Banking Transactions PBIP](https://github.com/taarikakanauji/bank-transactions-analysis/blob/main/Bank%20Transaction%20Report.pbip)  
- **Gitignore:** [.gitignore](https://github.com/taarikakanauji/bank-transactions-analysis/blob/main/.gitignore)  

### **Project README (Setup Guide)**  
[README.md](https://github.com/taarikakanauji/bank-transactions-analysis/blob/main/README.md)  

# Conclusion

This dashboard empowers stakeholders to:
- Identify banking transactions insights
- Spot regional opportunities (invest in the West and Europe, improve the East and Asia)
- Increase security and reduce fraudulent transactions
- Optimize Mobile performance and explore potential customer conversion from Desktop to Mobile

By leveraging these insights, the bank can allocate resources more effectively, boost profitability, and address underperforming areas.


