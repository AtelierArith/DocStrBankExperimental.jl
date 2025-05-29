```
readFamaFrench(ffn;kwargs...)
```

`ffn` can be the table name (in which case it is retreived from the web) or a path to the local file. `kwargs` are passed to `CSV.File`. Missing values (`-99.99` or `-999`) are replaced with `missing`.

Returns three pieces:

```
- `tables::Vector{DataFrame}` - the extracted tables

- `tablenotes::Vector{String}` - any notes to the tables

- `filenotes::String` - notes at the top of the file
```

Example Usage:

```julia
using DataFrames, FamaFrenchData

# read the Fama-French 3 factors (monthly and annual)
tables, tablenotes, filenotes = readFamaFrench("F-F_Research_Data_Factors")

# read the Fama-French 3 factors (daily)
tablesd, tablenotesd, filenotesd = readFamaFrench("F-F_Research_Data_Factors_Daily")

# read the 25 Size-B/M portfolios (monthly and annual)
tables25, tablenotes25, filenotes25 = readFamaFrench("25_Portfolios_5x5")
```
