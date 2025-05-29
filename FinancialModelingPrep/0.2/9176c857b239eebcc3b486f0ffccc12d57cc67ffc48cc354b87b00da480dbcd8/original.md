```
mutual_fund_holders(fmp, symbol)
```

Returns the mutual fund holders of a specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Mutual-Fund-Holders](https://site.financialmodelingprep.com/developer/docs/#Mutual-Fund-Holders) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the mutual fund holders of AAPL
data = mutual_fund_holders(fmp, "AAPL")
```
