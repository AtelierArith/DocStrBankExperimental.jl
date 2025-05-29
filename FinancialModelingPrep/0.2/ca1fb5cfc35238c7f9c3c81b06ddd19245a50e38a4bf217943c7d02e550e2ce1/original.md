```
institution_search(fmp, name)
```

Returns all CIKs matching the specified institution name.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `name::String`: An institution name.

See [Institutional-Holders-Search](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holders-Search) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the CIKs for Berkshire Hathaway
data = institution_search(fmp, name = "Berkshire%20Hathaway%20Inc")
```
