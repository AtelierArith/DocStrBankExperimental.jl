```
senate_trades_feed(fmp, params...)
```

Returns senate trades from the RSS feed.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Senate-Trading-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#Senate-trading) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of senate trades from the RSS feed
data = senate_trades_feed(fmp, page = 0)
```
