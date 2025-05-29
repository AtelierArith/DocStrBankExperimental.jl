```
discounted_cash_flows(fmp, symbol)
```

Returns discounted cash flows for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Discounted-Cash-Flow](https://site.financialmodelingprep.com/developer/docs/#Company-Discounted-cash-flow-value) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the dcf for AAPL
data = discounted_cash_flows(fmp, "AAPL")
```
