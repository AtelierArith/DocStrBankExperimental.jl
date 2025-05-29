```
stock_grades(fmp, symbol, params...)
```

Returns stock grades for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Stock-Grade](https://site.financialmodelingprep.com/developer/docs/#Stock-Grade) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the last 100 stock grades for AAPL
data = stock_grades(fmp, "AAPL", limit = 100)
```
