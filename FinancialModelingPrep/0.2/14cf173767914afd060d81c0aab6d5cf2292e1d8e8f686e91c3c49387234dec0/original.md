```
available_euronext(fmp)
```

Returns all available euronext symbols in the API.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Euronext-List](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-EuroNext) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all available euronext symbols
data = available_euronext(fmp)
```
