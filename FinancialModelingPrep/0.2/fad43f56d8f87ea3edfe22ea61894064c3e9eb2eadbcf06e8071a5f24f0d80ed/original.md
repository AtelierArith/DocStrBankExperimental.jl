```
available_countries(fmp)
```

Returns a JSON array of all available countries in the API.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Stock-Screener](https://site.financialmodelingprep.com/developer/docs/#Stock-Screener) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all available countries
data = available_countries(fmp)
```
