```
social_sentiment_trends(fmp, type, source)
```

Returns a JSON table with the social sentiment trends for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `type::String:` One of "bullish" or "bearish".
  * `source::String:` One of "twitter" or "stocktwits".

See [Social-Sentiment](https://site.financialmodelingprep.com/developer/docs/#Social-Sentiment) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all social sentiment trends
data = social_sentiment_trends(fmp)

# get all social sentiment trends from stocktwits with a bearish bias
data = social_sentiment_trends(fmp, type = "bearish", source = "stocktwits")
```
