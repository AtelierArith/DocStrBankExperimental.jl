```
insiders_list(fmp, params...)
```

Returns all insider names and their CIKs matching the specified parameters.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [CIK-Mapper](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all insider names and their CIKs from page 3
data = insiders_list(fmp, page = 3)
```
