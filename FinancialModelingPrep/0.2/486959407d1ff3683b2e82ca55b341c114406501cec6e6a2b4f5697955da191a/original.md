```
fails_to_deliver(fmp, symbol, params)
```

Returns fails to deliver for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Fails-to-Deliver](https://site.financialmodelingprep.com/developer/docs/#Fail-to-deliver) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of fails to deliver for AAPL
data = fails_to_deliver(fmp, "AAPL", page = 0)
```
