```
stock_news(fmp, params...)
```

Returns stock news articles.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Stock-News](https://site.financialmodelingprep.com/developer/docs/#Stock-News) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the latest 50 stock news for AAPL and FB
data = stock_news(fmp, tickers = "AAPL,FB", limit = 50)
```
