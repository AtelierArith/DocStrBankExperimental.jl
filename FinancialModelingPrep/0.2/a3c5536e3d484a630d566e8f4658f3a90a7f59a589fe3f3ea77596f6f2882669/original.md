```
mergers_and_acquisitions_feed(fmp, params...)
```

Returns a JSON table containing the mergers and acquisitions feed results.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Mergers-and-Acquisitions-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#MERGER-AND-ACQUISITION) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of the mergers and acquisitions rss feed
data = mergers_and_acquisitions_feed(fmp, page = 0)
```
