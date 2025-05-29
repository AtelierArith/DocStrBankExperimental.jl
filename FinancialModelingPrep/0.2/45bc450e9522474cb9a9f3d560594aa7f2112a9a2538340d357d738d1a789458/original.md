```
shares_float(fmp)
shares_float(fmp, symbol)
```

Returns shares float statistics for one or all symbols.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol or all symbols if not provided.

See [Shares-Float](https://site.financialmodelingprep.com/developer/docs/#Shares-Float) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get shares float for all symbols
data = shares_float(fmp)

# get shares float for AAPL
data = shares_float(fmp, "AAPL")
```
