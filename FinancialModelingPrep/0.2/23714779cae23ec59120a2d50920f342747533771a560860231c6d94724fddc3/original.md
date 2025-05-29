```
etf_symbols(fmp)
```

Returns all tradeable symbols in the API.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [ETF-Symbols](https://site.financialmodelingprep.com/developer/docs/#ETF-List) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all etf symbols
data = etf_symbols(fmp)
```
