```
stock_screener(fmp, params...)
```

Returns search results for the specified filters.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Stock-Screener](https://site.financialmodelingprep.com/developer/docs/#Stock-Screener) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all tech stocks in the NASDAQ with a market cap over 100mm and a beta above 1
data = stock_screener(fmp, marketCapMoreThan = 100000000, betaMoreThan = 1, sector = "Technology", exchange = "NASDAQ")

# get the first 100 stocks in California with a price greater than 100
data = stock_screener(fmp, country = "CA", priceMoreThan = 100, limit = 100)
```
