```
available_commodities(fmp)
```

Returns all available commodities in the API.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Commodities-List](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-Major-Commodities-(Gold,-Silver,-Oil)) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all available commodities
data = available_commodities(fmp)
```
