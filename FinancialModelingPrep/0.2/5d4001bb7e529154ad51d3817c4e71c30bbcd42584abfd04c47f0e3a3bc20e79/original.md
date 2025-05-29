```
historical_splits(fmp, symbol)
```

Returns the historical stock splits for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Historical-Stock-Splits](https://site.financialmodelingprep.com/developer/docs/#Historical-Stock-Splits) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the historical splits for AAPL
data = historical_splits(fmp, "AAPL")
```
