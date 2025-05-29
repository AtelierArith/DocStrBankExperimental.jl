```
advanced_discounted_cash_flows(fmp, symbol, levered = false)
```

Returns advaned discounted cash flows for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `levered::Bool`: Return the levered dcf with including WACC.

See [Discounted-Cash-Flow](https://site.financialmodelingprep.com/developer/docs/#Company-Discounted-cash-flow-value) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the levered dcf for AAPL with WACC
data = advanced_discounted_cash_flows(fmp, "AAPL", levered = true)
```
