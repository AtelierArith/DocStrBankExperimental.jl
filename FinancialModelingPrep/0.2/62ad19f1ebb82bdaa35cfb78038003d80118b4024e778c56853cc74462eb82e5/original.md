```
price_targets_consensus(fmp, symbol)
```

Returns the price targets consensus for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Price-Target-Consensus](https://site.financialmodelingprep.com/developer/docs/#Price-Target-Consensus) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the price targets consensus for AAPL
data = price_target_consensus(fmp, "AAPL")
```
