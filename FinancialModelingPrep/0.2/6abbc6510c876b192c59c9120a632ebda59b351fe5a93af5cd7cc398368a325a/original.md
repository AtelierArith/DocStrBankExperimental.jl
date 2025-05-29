```
institutional_ownership_percentages(fmp, symbol, params...)
```

Returns institutional ownership percentages for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Stock-Ownership-by-Holders](https://site.financialmodelingprep.com/developer/docs/#Stock-Ownership-by-Holders) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the institutional ownership percentages for AAPL in Q3 of 2021
data = institutional_ownership_percentages(fmp, "AAPL", date = "2021-09-30")
```
