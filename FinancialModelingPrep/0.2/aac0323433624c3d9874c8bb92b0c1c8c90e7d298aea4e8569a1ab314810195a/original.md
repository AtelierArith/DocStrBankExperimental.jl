```
cik_from_symbol(fmp, symbol)
```

Returns all CIKs matching the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [CIK-Mapper](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the CIK for AAPL
data = cik_from_symbol(fmp, "AAPL")
```
