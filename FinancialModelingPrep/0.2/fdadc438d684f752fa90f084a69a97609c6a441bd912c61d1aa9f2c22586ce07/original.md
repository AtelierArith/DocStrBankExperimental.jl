```
stock_news_sentiment_feed(fmp, params...)
```

Returns stock news article sentiment.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Stock-Sentiment](https://site.financialmodelingprep.com/developer/docs/#Stock-News) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of stock news article sentiment
data = stock_news_sentiment_feed(fmp, page = 0)
```
