```
financial_scores(fmp, symbol)
```

Returns common financial scores for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Financial-Scores](https://site.financialmodelingprep.com/developer/docs/#Stock-Financial-scores) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get financial scores for AAPL
data = financial_scores(fmp, "AAPL")
```
