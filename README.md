# Calgary-School-Enrollment-Analytics
Power BI dashboard analyzing Calgary school enrollment trends using Microsoft Fabric, Dataflows and Power BI Desktop

This project provides a comprehensive end-to-end analytics solution for understanding school enrollment patterns across Calgary, utilizing Microsoft Fabric, Dataflows, a Lakehouse, a Semantic Model, and Power BI visualizations.

The report delivers actionable insights, trends, comparisons, forecasts, and school performance metrics that help stakeholders make informed decisions about education planning and resource allocation.

Project Overview

This analytics project explores enrollment trends across different school categories in Calgary:

Public Schools

Separate Schools

Private Schools

Charter Schools

It answers key questions such as:

Which schools have the highest and lowest enrollment?

How has enrollment changed year over year?

Which school category has the highest share of students?

What are the growth trends over the last decade?

Which schools show the strongest or weakest YoY performance?

The solution is built using Microsoft Fabric Lakehouse, Dataflow Gen2, Semantic Model and Power BI for visualization.

Architecture & Workflow
1.  Data Storage — Microsoft Fabric Lakehouse

Source Excel/CSV files uploaded into a Fabric Lakehouse.

Table stored as “managed Delta tables” for reliability & performance.

2️. Data Transformation — Dataflow Gen2

The dataflow performs:

Column renaming

Data typing

Removing blanks

Filtering years

Creating measures for enrollment calculations

Transforming tables for Power BI

3. Data Modeling — Semantic Model

Relationship modeling

Creating DAX measures

Creating Hierarchy, formatting and Descriptions

Designing report pages (Visualisation) - Power BI 

Two fully designed report pages:

Executive Summary Dashboard

Comparative Insights


Report Pages
 Page 1 – Executive Summary

Highlights:

Total enrollment

Number of schools

Average enrollment per school

Year-over-year % change

Enrollment trends with forecast

Division-level comparisons

Top 5 schools by enrollment

Distribution by school category

YoY gauge vs target

Page 2 – Comparative Insights

Includes:

Detailed school enrollment table

Table summary by category

Category totals

Enrollment type trends

Insights 



Key DAX Measures
Total Enrollment
Total Enrollment = SUM(Enrollment[TotalEnrollment])

Year-over-Year % Growth
YoY % = 
VAR PrevYear = CALCULATE([Total Enrollment], DATEADD(Enrollment[StartYear], -1, YEAR))
RETURN
DIVIDE([Total Enrollment] - PrevYear, PrevYear)

Largest School
Largest School Name =
VAR MaxValue = MAXX(ALL(Enrollment), [Total Enrollment])
RETURN
CALCULATE(SELECTEDVALUE(Enrollment[SchoolName]), [Total Enrollment] = MaxValue)

Smallest School
Smallest School Name =
VAR MinValue = MINX(ALL(Enrollment), [Total Enrollment])
RETURN
CALCULATE(SELECTEDVALUE(Enrollment[SchoolName]), [Total Enrollment] = MinValue)

Highest YoY Growth School
Highest YoY Growth School =
VAR TopVal = MAXX(ALL(Enrollment), [YoY %])
RETURN
CALCULATE(SELECTEDVALUE(Enrollment[SchoolName]), [YoY %] = TopVal)

Lowest YoY Growth School
Lowest YoY Growth School =
VAR BottomVal = MINX(ALL(Enrollment), [YoY %])
RETURN
CALCULATE(SELECTEDVALUE(Enrollment[SchoolName]), [YoY %] = BottomVal)

 
📁 Files Included

Power BI Report (.pbix)

Dashboard screenshots

Measures screenshot

Dataflow Screenshot

Semantic Model Screenshot

Key Skills Demonstrated

Microsoft Fabric Lakehouse

Dataflow Gen2 transformations

Power BI data modeling

Advanced DAX calculations

Forecasting analytics

Dashboard UX/UI design

Version control with GitHub

Future Improvements

Automate data refresh via Fabric pipelines

Integrate with Azure Synapse 

Author

Obianuju Lynda Nzurumike
Data Analyst | Data Engineer
Calgary, Alberta
nzurumikeuju@yahoo.com
LinkedIn: https://www.linkedin.com/in/obianuju-nzurumike/



Data Source & Usage License

The dataset used in this project comes from publicly available sources.
All rights and original data ownership belong to the data providers listed below.

Source: Calgary School Enrollment Data

Provider: Calgary Board of Education / City of Calgary Open Data

License: Open Government License – Canada (OGL-Canada)

Usage: The dataset is free to use, modify, and publish with attribution.

This project uses open data made available under the Open Government License – Canada.
