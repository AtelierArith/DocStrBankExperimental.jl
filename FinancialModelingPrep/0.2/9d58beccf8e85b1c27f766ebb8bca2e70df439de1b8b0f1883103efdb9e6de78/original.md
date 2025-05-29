```
forex_news(fmp, params...)
```

Returns forex news articles.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Forex-News](https://site.financialmodelingprep.com/developer/docs/#Forex-news) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of news for EURUSD
data = forex_news(fmp, symbol = "EURUSD", page = 0)
```
