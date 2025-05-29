```
upgrades_and_downgrades(fmp, symbol)
```

Returns upgrades and downgrades for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Upgrades-&-Downgrades](https://site.financialmodelingprep.com/developer/docs/#Upgrades-&-Downgrades) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the upgrades and downgrades for AAPL
data = upgrades_and_downgrades(fmp, AAPL)
```
