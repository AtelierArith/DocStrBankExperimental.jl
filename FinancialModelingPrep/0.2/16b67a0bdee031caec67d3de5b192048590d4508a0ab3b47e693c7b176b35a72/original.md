```
crypto_news(fmp, params...)
```

Returns crypto news articles.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Crypto-News](https://site.financialmodelingprep.com/developer/docs/#Crypto-news) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of news for BTCUSD
data = crypto_news(fmp, symbol = "BTCUSD", page = 0)
```
