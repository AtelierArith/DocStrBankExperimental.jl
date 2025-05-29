```
price_change(fmp, symbol)
```

Returns the price change for the specified symbol(s).

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Price-Change](https://site.financialmodelingprep.com/developer/docs/#Stock-price-change) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the price change for AAPL
data = price_change(fmp, "AAPL")
```
