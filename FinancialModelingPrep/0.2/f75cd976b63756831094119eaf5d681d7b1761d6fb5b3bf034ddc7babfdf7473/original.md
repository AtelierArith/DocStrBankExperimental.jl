```
price_targets(fmp, symbol)
```

Returns price targets for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Price-Target](https://site.financialmodelingprep.com/developer/docs/#Price-Target) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the price targets for AAPL
data = price_targets(fmp, "AAPL")
```
