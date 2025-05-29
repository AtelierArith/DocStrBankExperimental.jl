```
institutions_list(fmp)
```

Returns all companies by CIK.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Institutions-List](https://site.financialmodelingprep.com/developer/docs/#Form-13F) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all institutions
data = institutions_list(fmp)
```
