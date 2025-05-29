```
stock_peers(fmp, symbol)
```

Returns a JSON array of the stock peers for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Stock-Peers](https://site.financialmodelingprep.com/developer/docs/#Stock-Peers) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the stock peers for AAPL
data = stock_peers(fmp, "AAPL")
```
