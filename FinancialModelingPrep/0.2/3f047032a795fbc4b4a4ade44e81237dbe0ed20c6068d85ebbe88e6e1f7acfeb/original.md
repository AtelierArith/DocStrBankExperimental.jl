```
institutional_ownership_feed(fmp, params...)
```

Returns institutional ownership from the RSS feed.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Institutional-Holder-Rss-Feed](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holder-Rss-Feed) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of results from the RSS feed
data = institutional_ownership_feed(fmp, page = 0)
```
