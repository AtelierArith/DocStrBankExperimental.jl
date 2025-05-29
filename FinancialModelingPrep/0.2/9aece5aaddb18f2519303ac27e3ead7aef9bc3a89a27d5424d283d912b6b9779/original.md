```
esg_scores(fmp, symbol)
```

Returns a JSON table with the ESG scores for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [ESG-Score](https://site.financialmodelingprep.com/developer/docs/#ESG-SCORE) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the esg scores for AAPL
data = esg_scores(fmp, "AAPL")
```
