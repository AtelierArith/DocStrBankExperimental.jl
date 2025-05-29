```
fmp_articles(fmp, params...)
```

Returns a JSON object of fmp articles.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [FMP-Articles](https://site.financialmodelingprep.com/developer/docs/#FMP-Articles) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get fmp articles from page 0 and size 5
data = fmp_articles(fmp, page = 0, size = 5)
```
