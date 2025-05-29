```
etf_summary(fmp, symbol)
```

Returns the etf summary for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [ETF-Info](https://site.financialmodelingprep.com/developer/docs/#ETF-Expense-ratio) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the etf summary for SPY
data = etf_summary(fmp, "SPY")
```
