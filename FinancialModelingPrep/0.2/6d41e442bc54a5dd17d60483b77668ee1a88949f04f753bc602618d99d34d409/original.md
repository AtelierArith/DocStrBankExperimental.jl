```
key_executives(fmp, symbol)
```

Returns the key executives for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Key-Executives](https://site.financialmodelingprep.com/developer/docs/#Key-Executives) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the key executives for AAPL
data = key_executives(fmp, "AAPL")
```
