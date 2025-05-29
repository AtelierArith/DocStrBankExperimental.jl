```
historical_discounted_cash_flows(fmp, symbol, params...)
```

Returns historical discounted cash flows for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Historical-Discounted-Cash-Flow](https://site.financialmodelingprep.com/developer/docs/#Company-Discounted-cash-flow-value) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the dcf for in the last 30 quarters AAPL
data = historical_discounted_cash_flows(fmp, "AAPL", period = "quarter", limit = 30)
```
