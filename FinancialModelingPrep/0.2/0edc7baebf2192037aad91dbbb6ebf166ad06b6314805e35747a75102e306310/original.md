```
cik_from_insider(fmp, name)
```

Returns all CIKs matching the specified insider name.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `name::String`: A name.

See [CIK-Mapper](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all CIKs matching "zuckerberg mark"
data = cik_from_insider(fmp, "zuckerberg%20mark")
```
