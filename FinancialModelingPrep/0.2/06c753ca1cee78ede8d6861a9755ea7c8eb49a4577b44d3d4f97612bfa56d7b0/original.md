```
beneficial_ownership(fmp, symbol)
```

Returns beneficial ownership for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Individual-Beneficial-Ownership](https://site.financialmodelingprep.com/developer/docs/#Individual-Beneficial-Ownership) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the beneficial ownership for AAPL
data = beneficial_ownership(fmp, "AAPL")
```
