```
owners_earnings(fmp, symbol)
```

Returns owners earnings for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Owners-Earnings](https://site.financialmodelingprep.com/developer/docs/#Stock-Financial-scores) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get ownings earnings for AAPL
data = owners_earnings(fmp, "AAPL")
```
