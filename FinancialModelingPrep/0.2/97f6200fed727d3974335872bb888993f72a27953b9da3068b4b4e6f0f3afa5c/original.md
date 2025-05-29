```
senate_trades(fmp, symbol)
```

Returns senate trades for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Senate-Trading](https://site.financialmodelingprep.com/developer/docs/#Senate-trading) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get senate trades for AAPL
data = senate_trades(fmp, "AAPL")
```
