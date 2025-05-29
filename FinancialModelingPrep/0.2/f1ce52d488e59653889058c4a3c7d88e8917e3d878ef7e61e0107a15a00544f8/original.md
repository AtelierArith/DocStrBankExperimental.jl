```
institutional_holders(fmp, symbol)
```

Returns the institutional holders of a specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Institutional-Holders](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holders) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the institutional holders of AAPL
data = institutional_holders(fmp, "AAPL")
```
