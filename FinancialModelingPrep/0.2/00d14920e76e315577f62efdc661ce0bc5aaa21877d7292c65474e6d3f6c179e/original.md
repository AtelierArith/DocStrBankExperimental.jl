```
crowdfunding_offerings_feed(fmp, params...)
```

Returns crowdfunding offerings from the RSS feed.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Crowdfunding-Offerings-Rss-Feed](https://site.financialmodelingprep.com/developer/docs/#Crowdfunding-Offerings-Rss-feed) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of results from the RSS feed
data = crowdfunding_offerings_feed(fmp, page = 0)
```
