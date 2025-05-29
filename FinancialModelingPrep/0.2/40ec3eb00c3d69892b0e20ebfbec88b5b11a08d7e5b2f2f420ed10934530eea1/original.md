```
available_symbols(fmp)
```

Returns all available symbols in the API.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Symbols-List](https://site.financialmodelingprep.com/developer/docs/#Symbols-List) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all available symbols
data = available_symbols(fmp)
```
