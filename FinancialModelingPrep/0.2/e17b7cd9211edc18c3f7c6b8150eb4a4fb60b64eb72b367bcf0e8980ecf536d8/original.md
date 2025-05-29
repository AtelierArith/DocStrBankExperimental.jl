```
most_active(fmp)
```

Returns the most active symbols.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Most-Active](https://site.financialmodelingprep.com/developer/docs/#Most-Active-Stock-Companies) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the most active symbols
data = most_active(fmp)
```
