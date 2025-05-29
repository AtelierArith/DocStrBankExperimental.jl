function wdi(indicators::Union{String,Array{String,1}}, countries::Union{String,Array{String,1}}, startyear::Integer=-1, endyear::Integer=-1; extra::Bool=false, sourceid::Integer=2, dflong::Bool=false, verbose::Bool=false)::DataFrame

Download data from World Development Indicators (WDI) Data Catalog of the World Bank.

https://datacatalog.worldbank.org/dataset/world-development-indicators

# Arguments

  * `indicators` : indicator name or array of indicators
  * `countries` : string or string array of ISO 2 or ISO 3 letter country codes or `all` for all countries.
  * `startyear` : first year to include
  * `endyear` : last year to include (required if startyear is set)
  * `extra` : if `true` additional country data should be included (region, capital, longitude, latitude, income, lending)
  * `sourceid` : source number, see https://api.worldbank.org/v2/sources
  * `dflong` : long dataframe format. default is wide. with many indicators `long` might be easier to work with.
  * `verbose` : if `true` print URLs downloaded

# Examples

```julia
df = wdi("SP.POP.TOTL", "US")
df = wdi("SP.POP.TOTL", "US", 1980, 2012)
df = wdi("SP.POP.TOTL", "USA", 1980, 2012, extra=true)
df = wdi("SP.POP.TOTL", "all", 2000, 2000, verbose=true, extra=true)
df = wdi("SP.POP.TOTL", ["US","BR"], 1980, 2012, extra=true)
df = wdi(["SP.POP.TOTL", "NY.GDP.MKTP.CD"], ["US","BR"], 1980, 2012, extra=true)
df = wdi(["SP.POP.TOTL", "NY.GDP.MKTP.CD"], ["US","BR"], 1980, 2012, dflong=true)
```
