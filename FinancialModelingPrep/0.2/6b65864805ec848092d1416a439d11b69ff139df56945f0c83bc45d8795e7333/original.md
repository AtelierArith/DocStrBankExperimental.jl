```
general_news(fmp, params...)
```

Returns general news articles.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [General-News](https://site.financialmodelingprep.com/developer/docs/#General-news) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of general news
data = general_news(fmp, page = 0)
```
