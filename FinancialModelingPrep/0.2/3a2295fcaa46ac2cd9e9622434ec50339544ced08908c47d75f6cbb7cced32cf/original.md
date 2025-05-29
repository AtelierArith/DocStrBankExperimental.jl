```
historical_dividends(fmp, symbol)
```

Returns a JSON table historical dividends for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Historical-Dividends](https://site.financialmodelingprep.com/developer/docs/#Historical-Dividends) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the last historical dividends for AAPL
data = historical_dividends(fmp, "AAPL")
```
