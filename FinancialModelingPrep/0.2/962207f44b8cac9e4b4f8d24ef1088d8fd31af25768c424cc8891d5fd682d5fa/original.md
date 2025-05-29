```
search_name(fmp, name, params...)
```

Returns search results for the specified name and filters.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `name::String`: A company name.
  * `params...`: Additional keyword query params.

See [Name-Search](https://site.financialmodelingprep.com/developer/docs/#Ticker-Search) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first 10 matches where name is Meta and exchange is NASDAQ
data = search_name(fmp, "Meta", limit = 10, exchange = "NASDAQ")
```
