```
otc_quote(fmp, symbol)
```

Returns the price quote for the specified symbol(s).

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [OTC-Quote](https://site.financialmodelingprep.com/developer/docs/#Company-Quote) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the otc quote for GBTC
data = otc_quote(fmp, "GBTC")
```
