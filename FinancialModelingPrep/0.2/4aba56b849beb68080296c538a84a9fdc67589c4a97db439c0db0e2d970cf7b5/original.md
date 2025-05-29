```
delisted_companies(fmp, params...)
```

Returns delisted companies.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Delisted-Companies](https://site.financialmodelingprep.com/developer/docs/#Delisted-Companies) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of delisted companies
data = delisted_companies(fmp, page = 0)
```
