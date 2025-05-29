```
esg_ratings(fmp, symbol)
```

Returns a JSON table with the ESG ratings for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [ESG-Ratings](https://site.financialmodelingprep.com/developer/docs/#Company-ESG-Risk-Ratings) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the esg ratings for AAPL
data = esg_ratings(fmp, "AAPL")
```
