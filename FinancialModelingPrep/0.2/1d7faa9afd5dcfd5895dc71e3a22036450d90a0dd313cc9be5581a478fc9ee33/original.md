```
senate_disclosure_feed(fmp, params...)
```

Returns senate disclosures from the RSS feed.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Senate-Disclosure-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#Senate-disclosure) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of senate disclosures from the RSS feed
data = senate_disclosure_feed(fmp, page = 0)
```
