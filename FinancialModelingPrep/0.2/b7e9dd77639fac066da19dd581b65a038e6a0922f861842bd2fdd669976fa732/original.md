```
upgrades_and_downgrades_feed(fmp, params...)
```

Returns upgrades and downgrades from the rss feed.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Upgrades-&-Downgrades-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#Upgrades-&-Downgrades-RSS-Feed) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of upgrades and downgrades
data = upgrades_and_downgrades_feed(fmp, page = 0)
```
