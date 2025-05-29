```
equity_offerings_feed(fmp, params...)
```

Returns equity offerings from the RSS feed.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Equity-Offerings-Fundraising-Rss-feed](https://site.financialmodelingprep.com/developer/docs/#Equity-offerings-Fundraising-Rss-feed) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of results from the RSS feed
data = equity_offerings_feed(fmp, page = 0)
```
