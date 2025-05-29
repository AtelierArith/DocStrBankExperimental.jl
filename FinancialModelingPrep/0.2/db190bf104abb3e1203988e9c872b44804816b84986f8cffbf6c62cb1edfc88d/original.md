```
economic_indicator(fmp, name, params...)
```

Returns the treasury rates for the specified date range.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `name::String`: An econmic indicator.
  * `params...`: Additional keyword query params.

See [Economic-Indicator](https://site.financialmodelingprep.com/developer/docs/#Economic-Indicator) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the real GDP for Q1 2022
data = economic_indicator(fmp, name = "realGDP", from = "2022-01-01", to = "2022-03-31")

# get the federal funds rate for Q1 2022
data = economic_indicator(fmp, name = "federalFunds", from = "2022-01-01", to = "2022-03-31")
```
