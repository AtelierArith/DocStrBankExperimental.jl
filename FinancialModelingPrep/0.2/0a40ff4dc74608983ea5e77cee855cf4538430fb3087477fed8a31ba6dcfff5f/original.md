```
historical_ratings(fmp, symbol, params...)
```

Returns historical ratings for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Historical-Ratings](https://site.financialmodelingprep.com/developer/docs/#Company-Rating) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the last 100 ratings for AAPL 
data = historical_ratings(fmp, "AAPL", limit = 100)
```
