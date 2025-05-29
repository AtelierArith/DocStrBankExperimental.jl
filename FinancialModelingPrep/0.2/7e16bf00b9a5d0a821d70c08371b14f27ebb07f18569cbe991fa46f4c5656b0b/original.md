```
available_forex_pairs(fmp)
```

Returns all available forex pairs in the API.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Forex-Pairs-List](https://site.financialmodelingprep.com/developer/docs/#Forex-(FX)) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all available forex pairs
data = available_forex_pairs(fmp)
```
