# Project: Personal Information

## Description of Project
We need a PHP solution to parse this HTML file uploaded by our family members. Each file will follow the same format, but the number of records inside may vary. Parsed data will be saved into a PostgreSQL database.

## Requirements
* validate file size
* validate by HTML MIME type
* temporary storage can be used but must be terminated after successful storage
* delivered file needs to independently function without the assistance of frameworks
* vanilla PHP is the only acceptable approach
* no frameworks to be used (like Laravel or Slim)

We need to store all **personal information** records on our personal budget from month to month. We want to store them in a Postgres DB with the following column structure:

|Reference|Report Date|Type|ChesterPA|AllenTX|AtlantaGA|
|:-:|:-:|:-:|:-:|:-:|:-:|
|*VARCHAR(9)|*MM/DD/YYYY|VARCHAR(255)|VARCHAR(255)|VARCHAR(255)|VARCHAR(255)|

* From month to month we will not know how many inquiry records we'll have. Could be 1. Could 30. Could be 0.
* If 0, no record should be created. If ≤1, then create the corresponding record(s) in the DB.

*must always be present

**may sometimes be blank

***postgres db available upon request

## Data Table Selector
`#ctrlCreditReport > chesterpa-report > div.ng-binding.ng-scope > div:nth-child(7) > table.re-even-odd.rpt_content_table.rpt_content_header.rpt_table4column`

## Screenshot of Data Table in HTML
![Table Appears in HTML](file%20to%20be%20parsed%20-%20personalinformation.png?raw=true "Table Appears in HTML")

## Data Once Inputed to Postgres
This is a simple composite of how the data should appear in the PostgreSQL table after a successful INSERT has completed. The affected columns and subsequent records should appear as such:
|Reference|Report Date|Type|ChesterPA|AllenTX|AtlantaGA|
|:-:|:-:|:-:|:-:|:-:|:-:|
|M54898847|05/23/2024|Credit Report Date:|05/23/2024|05/23/2024|05/23/2024|
|M54898847|05/23/2024|Name:|LAMBERT  SKY  WHITE|-|LAMBERT  SKYLAR  WHITE|
|M54898847|05/23/2024|Also Known As:|WHITE,SKYLAR,L SKYLER  WHITE SKYLR  WHITE|LAMBERT  T  SKYLR|-|
|M54898847|05/23/2024|Former:|-|-|SKYYLER  WHITE LAMBERT  T  SKYLR SKYLR  WHITE LAMBERT  T  WHITE SKYLAR  M  WHITE|
|M54898847|05/23/2024|Date of Birth:|08/11/1970|1970|08/11/1970|
|M54898847|05/23/2024|Current Address(es):|3320 BRUNCHBERRY LN ALBUQUERQUE, NM 87111|3828 PIERMONT DRIVE DR ALBUQUERQUE, NM 87111-4189 05/2024|3828 PIERMONT DRIVE DR ALBUQUERQUE, NM 87111|
|M54898847|05/23/2024|Previous Address(es):|3828 PIERMONT DRIVE DR ALBUQUERQUE, NM 87111 308 NEGRA ARROYO LANE ALBUQUERQUE, NM 87104|308 NEGRA ARROYO LANE ALBUQUERQUE, NM 87104-6160 07/2020 3320 BRUNCHBERRY LN ALBUQUERQUE, NM 87111-3651 09/2020|308 NEGRA ARROYO LANE ALBUQUERQUE, NM 87104 1617 CANDELARIA ROAD ALBUQUERQUE, NM 87107|
|M54898847|05/23/2024|Employers:|A1A CAR WASH BENEKE FABRICATORS|BENEKE FABRICATORS INC A1A CAR WASH LLC|A1A CAR WASH BENEKE FABRICATORS BENEKE FABRICATORS INCORPORATED|

## Screenshot of Reference Table
This is a simple ER Diagram of the full table this data will be sent to in PostgreSQL. While all columns are shown here the only ones relevant to this project are found in the diagram ⬆.

![Table Appears in HTML](personalinformation_reference.png?raw=true "Table Appears in HTML")
