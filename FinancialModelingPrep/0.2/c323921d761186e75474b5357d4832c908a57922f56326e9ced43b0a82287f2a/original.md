```
price_targets_feed(fmp, params...)
```

Returns a JSON table containing the price targets feed results.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Price-Target-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#Price-Target-RSS-Feed) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page from the price target feed
data = price_targets_feed(fmp, page = 0)
```
