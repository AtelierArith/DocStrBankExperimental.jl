```
price_targets_summary(fmp, symbol)
```

Returns the price targets summary for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Price-Target-Summary](https://site.financialmodelingprep.com/developer/docs/#Price-target-Summary) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the price targets summary for AAPL
data = price_targets_summary(fmp, "AAPL")
```
