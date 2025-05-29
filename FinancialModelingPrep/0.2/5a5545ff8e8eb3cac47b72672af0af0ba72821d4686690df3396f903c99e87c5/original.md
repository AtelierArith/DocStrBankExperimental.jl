```
cik_search(fmp, name)
```

Returns all CIKs matching the specified name.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `name::String`: A complete or partial institution name.

See [Form-13F-Search](https://site.financialmodelingprep.com/developer/docs/#Form-13F) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all CIKs matching "Berkshire"
data = cik_search(fmp, name = "Berkshire")
```
