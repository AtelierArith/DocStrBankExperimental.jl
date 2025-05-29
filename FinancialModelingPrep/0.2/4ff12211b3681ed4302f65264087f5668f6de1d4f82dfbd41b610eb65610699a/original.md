```
enterprise_values(fmp, symbol, params...)
```

Returns enterprise value components for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Enterprise-Value](https://site.financialmodelingprep.com/developer/docs/#Company-Enterprise-Value) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get enterprise values for AAPL in the last 30 quarters
data = enterprise_values(fmp, "AAPL", period = "quarter", limit = 30)
```
