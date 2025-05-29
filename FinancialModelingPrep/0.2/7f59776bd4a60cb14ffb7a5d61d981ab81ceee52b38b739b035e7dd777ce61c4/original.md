```
tradeable_symbols(fmp)
```

Returns all tradeable symbols in the API.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Tradeable-Symbols-List](https://site.financialmodelingprep.com/developer/docs/#Tradable-Symbols-List) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all available symbols
data = tradeable_symbols(fmp)
```
