```
insider_trades_feed(fmp, params...)
```

Returns insider trades from the RSS feed.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Insider-Trading-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#Insider-Trading-RSS-Feed) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the most recent insider trades from the feed
data = insider_trades_feed(fmp, page = 0)
```
