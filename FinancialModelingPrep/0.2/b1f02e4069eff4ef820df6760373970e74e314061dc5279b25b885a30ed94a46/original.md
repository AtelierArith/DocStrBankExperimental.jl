```
historical_social_sentiment(fmp, symbol, params...)
```

Returns a JSON table with the historical social sentiment for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Social-Sentiment](https://site.financialmodelingprep.com/developer/docs/#Social-Sentiment) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of historical social sentiment for AAPL
data = historical_social_sentiment(fmp, "AAPL", page = 0)
```
