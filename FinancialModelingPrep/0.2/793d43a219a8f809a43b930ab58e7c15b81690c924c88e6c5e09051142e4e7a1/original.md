```
analyst_estimates(fmp, symbol, params...)
```

Returns analyst estimates for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Analyst-Estimates](https://site.financialmodelingprep.com/developer/docs/#Analyst-Estimates) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the last 4 quarters of analyst estimates for AAPL
data = analyst_estimates(fmp, "AAPL", period = "quarter", limit = 4)
```
