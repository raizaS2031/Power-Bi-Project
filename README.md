# Personal Finances-Dashboard

### Dashboard Link : https://app.powerbi.com/groups/me/reports/325b463b-df6f-4d0b-86bf-29edca3ccfb2?ctid=caca9011-7b6a-44de-861f-095a2ca883b7&pbi_source=linkShare&bookmarkGuid=51b18b10-b3cf-4f68-aa4f-0e8937d9aaa0

## Problem Statement



This report is useful for understanding personal finance behavior because it provides key information about income, expenses, expected earnings, and budgets. This allows for the creation of indicators that show the relationship between actual income and expected income, as well as the relationship between actual expenses and expected expenses, all over a specific period of time.

With this detailed understanding of personal finances, it becomes possible to identify areas for improvement, such as evaluating opportunities for saving or investing. It also facilitates the detection of expenses that could be affecting the establishment of healthy finances.


### Steps followed 

- Step 1 : Open the Excel file 'Finanzas' which contains 4 sheets: Ingresos, Gastos, Meta Ingresos y Presupuesto Gastos, from the Power BI browser to analyze the structure of our tables.
- Step 2 :  Change the table in the Presupuesto Gastos sheet of the Finanzas file to table format.
- Step 3 : Load data into Power BI Desktop, dataset is a .xlsx file.
- Step 4 : Data preparation from the query editor: add the custom column 'Tipo' to the Ingresos and Gastos tables, then merge both tables into a new table called 'Finanzas', where the 'Tipo' column indicates whether it is an expense or income.
- Step 5 :  Disable column unpivoting in the 'Meta Ingresos' table to store online income and remuneration in a new column called 'Categoría' and the amount for each in another column called 'Cantidad'.
- Step 6 : Add a new custom column called 'Tipo' to the 'Meta Ingresos' table containing the attribute 'Meta' to maintain the same format as the Ingresos and Gastos tables.
- Step 7 : Disable date column unpivoting in the 'Presupuesto Gastos' table to group them into one column called 'Fecha' and another called 'Cantidad' with the amount corresponding to each date.
- Step 8 :  Add a new custom column called 'Tipo' to the 'Presupuesto Gastos' table containing the attribute 'Presupuesto' to maintain the same format as the Ingresos, Gastos, and Meta Ingresos tables.
- Step 9 : Combine the 'Meta Ingresos' and 'Presupuesto Gastos' tables into a new table called 'Expectativas', which includes everything expected to be received and spent.
- Step 10: Hide the 4 previously loaded tables from the data model to make the two new tables 'Finanzas' and 'Expectativas' visible.
- Step 11: Create a line chart visualization from the 'Finanzas' table to observe the behavior of expenses and income by date, where we can see that from 2019 to 2020, income tends to increase and expenses tend to decrease.
- Step 12: Create a measure for future reference called 'Total Finanzas', which calculates the total sum of the 'Cantidad' field from the 'Finanzas' table.
           
           Total Finanzas = sum(Finanzas[Cantidad])
- Step 13 : From the 'Total Finanzas' measure, create a new measure called 'Ingresos' using the calculate function to filter the 'Ingresos' category from the 'Tipo' column of the 'Finanzas' table. 
           
           	Ingresos = CALCULATE([Total Finanzas],Finanzas[Tipo]="Ingresos")
A card visual was used to represent sum of Ingresos.  

![Ingresos](https://github.com/raizaS2031/Personal-Finances/assets/167453260/0b39d09b-1e4a-4be5-8d19-a90701a45c9e)

- Step 14 : From the 'Total Finanzas' measure, create a new measure called 'Gastos' using the calculate function to filter the 'Gastos' category from the 'Tipo' column of the 'Finanzas' table.
           
           	Gastos = CALCULATE([Total Finanzas],Finanzas[Tipo]="Gastos")
A card visual was used to represent sum of Gastos. 

![Gastos](https://github.com/raizaS2031/Personal-Finances/assets/167453260/26545442-fa3b-4f02-9f18-8df89d13747c)

- Step 15 : Create a measure for future reference called 'Total Expectativas', which calculates the total sum of the 'Cantidad' field from the 'Expectativas' table.
           
           	Total Expectativas = sum(Expectativas[Cantidad])

- Step 16 : From the 'Total Expectativas' measure, create a new measure called 'Presupuesto' using the calculate function to filter the 'Presupuesto' category from the 'Tipo' column of the 'Expectativas' table.
          
           	Presupuesto = CALCULATE([Total Expectativas],Expectativas[Tipo]="Presupuesto")
A card visual was used to represent sum of Presupuesto.

![Presupuesto](https://github.com/raizaS2031/Personal-Finances/assets/167453260/304df110-52a9-4181-a81d-cdd4a1fed53b)

- Step 17 : From the 'Total Expectativas' measure, create a new measure called 'Meta' using the calculate function to filter the 'Meta' category from the 'Tipo' column of the 'Expectativas' table.

          
           	Meta = CALCULATE([Total Expectativas],Expectativas[Tipo]="Meta")
A card visual was used to represent sum of Meta.

![Meta](https://github.com/raizaS2031/Personal-Finances/assets/167453260/dfe265a5-a15a-41a6-9c2a-1d46dfa9d9ad)

- Step 18 : Create a new measure called 'Utilidad', which is the result of subtracting Gastos from Ingresos. Add this new measure to the previous table.

          
           	utilidad = [Ingresos]-[Gastos]
A card visual was used to represent sum of Utilidad.

![utilidad](https://github.com/raizaS2031/Personal-Finances/assets/167453260/5ca24ffa-e033-48fb-ab6e-44ff514b1a57)

- Step 19 : Create a new measure called 'Utilidad Esperada', which is the result of subtracting Presupuesto from Meta. Add this new measure to the previous table.

          
           	Ut.esperada = [Meta]-[Presupuesto]
A card visual was used to represent sum of Utilidad Esperada.

![Ut  Esperada](https://github.com/raizaS2031/Personal-Finances/assets/167453260/c30b0003-a5f4-49df-8385-c4f353659a46)


          
           	As we can see, the Utilidad was greater than the Utilidad Esperada for 2019 and 2020.

![tabla info](https://github.com/raizaS2031/Personal-Finances/assets/167453260/0f50213f-83c1-4b9d-8d22-daf4d5821121)

Step 20 : Create a new table that will contain quota measures.

  (a) Cuota Ingresos

  (b) Cuota Gastos
  
  (c) Cuota Utilidad
  
  (d) Cuota Saldo
        
The quota measures can be represented in gauge visualizations as percentages.

Step 21 : Define the panels for the main page according to each quota. To interact with the information, insert date filters.

Step 22 :Create a new measure called 'Saldo', which is the sum of the utilidad up to the maximum date, i.e., what we have earned up to the current month.

          
           	Saldo = CALCULATE([utilidad],FILTER(ALL(Finanzas),Finanzas[Fecha]<=MAX(Finanzas[Fecha])))
A card visual was used to represent the sum of Saldo.

![Saldo](https://github.com/raizaS2031/Personal-Finances/assets/167453260/1398c8f3-2da7-4d84-b6c8-0bd1d456813a)

Step 23 : Create a new measure called 'Saldo Esperado', which is the sum of the utilidad esperada up to the maximum date, i.e., what we expect to have earned up to the current month.

          
           	Sa. Esperado = CALCULATE([Ut.esperada],FILTER(ALL(Expectativas),Expectativas[Fecha]<=MAX(Expectativas[Fecha])))
A card visual was used to represent the sum of Saldo Esperado.

![Sa  Esperado](https://github.com/raizaS2031/Personal-Finances/assets/167453260/f4f29933-2db8-49d6-87c9-fe67cd8a6e46)

           	As we can see in the table above, the Saldo was greater than the Saldo Esperado for the max date that is Dec 2020.

Step 24 : Create a new measure called 'cuota saldo', which is the proportion between Saldo and Saldo Esperado.

           	Cuota Saldo = [Saldo]/[Sa. Esperado]

Step 25 : Duplicate the main sheet to create sheet 2 and retain date filters and the Cuota Ingresos panel.

- Step 26: Create a table using Power BI's data entry option to differentiate categories belonging to online income and other types of income for all expenses.

- Step 27: Check in the data model that the relationship of the new 'Categoría' table has been correctly established with the 'Finanzas' and 'Expectativas' tables. In this way, hide the 'Categoría' field visibility from both tables to ensure that only the categories from the new 'Categoría' table appear.

- Step 28: On sheet 2, use the combo chart visualization to identify the quota of income, income, and meta by category of online income and other types of income.

- Step 29: On sheet 2, insert an area chart with the quota of income by date.

- Step 30: On sheet 2, insert a line chart with the quota of income by date, and use the legend to distinguish the category to identify if the income was from online or other types.

- Step 31: Edit interactions between visualizations to set those that need to change according to the selected year and month.

- Step 32: Edit slicers to synchronize sheet 2 with the main sheet, so that the selected date applies to both sheets.

- Step 33: Add navigation buttons between pages on page 2, as well as a button to move to the income detail sheet.

- Step 34: Within the income detail sheet, we can add visualizations such as:

(a) Bar charts comparing online income against others.
(b) Tables containing columns for income, meta, and income quota.

- Step 35: Perform a similar analysis as in sheet 2 for expense quota, utility quota, and balance quota.

- Step 36: Add buttons on the main sheet panels to enhance interaction from any mobile device.

- Step 37: Hide the created sheets to encourage the use of bookmarks.

- Step 38 : The report was then published to Power BI Service.


![publish](https://github.com/raizaS2031/Personal-Finances/assets/167453260/b5cb6942-a05c-4b2e-9507-c0c59f1e27b0)

# Snapshot of Dashboard (Power BI Service)

![dashboard_snap](https://github.com/raizaS2031/Personal-Finances/assets/167453260/158a8743-9b74-4509-9167-27d87446ad5b)

 
 # Report Snapshot (Power BI DESKTOP)

 
![dashboard_desktop](https://github.com/raizaS2031/Personal-Finances/assets/167453260/62346f7e-d328-4936-9841-0863dfa2c7b3)

# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Income for 2019 and 2020 

   Income for 2019 = 230,000

   Income for 2020 = 265,000

        thus, the income for 2020 is higher than 2019.
           
### [2] Budget for 2019 and 2020
Budget for 2019 = 183,000

Budget for 2020 = 179,000

        the main expense was on food for both years 2019 and 2020..
  
  ### [3] Comparison Expected earnings vs Income 
  
 2019 & 2020

 a)Expected earnings: 122,400

 b)Income: 132,618

 ### [4] Some other insights
 
 ### Earning
 
 1.1) In 2029, 95% of the expected balance corresponds to the profit.

1.2) In 2020, 108% of the expected balance corresponds to the profit.

     thus, from 2019 to 2020, grater profit was obtained.

## Acknowledgements

 - [Curso Power BI – Análisis de Datos y Business Intelligence](https://www.udemy.com/share/101BNu3@L5qcgx-ltZ0o4M_gAKoCVvX7cz03JRVsjoOkDYa2oirP1A95_xkIF6t34y4VDtqX8A==/)


