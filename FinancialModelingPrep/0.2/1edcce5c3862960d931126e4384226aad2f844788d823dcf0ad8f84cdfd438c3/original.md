```
available_indexes(fmp)
```

Returns all available indexes.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Available-Indexes](https://site.financialmodelingprep.com/developer/docs/#Historical-stock-index-prices) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all available indexes
data = available_indexes(fmp)
```
