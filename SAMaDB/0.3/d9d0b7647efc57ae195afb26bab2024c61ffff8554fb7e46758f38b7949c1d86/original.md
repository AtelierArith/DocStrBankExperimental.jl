South Africa Macroeconomic Database API

A julia API providing access to a relational database with public macroeconomic data for South Africa, obtained from from the South African Reserve Bank (SARB) and Statistics South Africa (STATSSA), and updated on a weekly basis via the EconData (https://www.econdata.co.za/) platform and automated scraping of the SARB and STATSSA websites. The database is maintained at the Department of Economics at Stellenbosch University. The package is built around the DataFrames.jl library. Its contents are summarized as follows:

**Datasets providing information about the available data**

`datasources()`   - Data sources

`datasets()`      - Datasets

`series()`        - Series (can be queried by dataset)

**Retrieve the data from the database**

`data()`          - By default retrieves all data

**Functions to reshape data and add temporal identifiers**

`pivot_wider()`   - Wrapper around DataFrames.unstack()

`pivot_longer()`  - Wrapper around DataFrames.stack()

`expand_date()`   - Create year, quarter, month and day columns from a date

**Helper functions to convert inputs to date strings**

`as_date()`       - E.g. "2011M01" -> "2011-01-01"

**Sting vectors with identifiers**

`SAMADB_ID`       - Cross-sectional identifiers

`SAMADB_T`        - Temporal identifiers
