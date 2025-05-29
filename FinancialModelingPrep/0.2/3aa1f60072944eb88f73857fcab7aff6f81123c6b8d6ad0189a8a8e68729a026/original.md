```
symbol_changes(fmp)
```

Returns changed symbols.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Symbol-Change](https://site.financialmodelingprep.com/developer/docs/#Symbol-Change) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get symbol changes
data = symbol_changes(fmp)
```
