```
available_tsx(fmp)
```

Returns all available tsx symbols in the API.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [TSX-List](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-TSX) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all available tsx symbols
data = available_tsx(fmp)
```
