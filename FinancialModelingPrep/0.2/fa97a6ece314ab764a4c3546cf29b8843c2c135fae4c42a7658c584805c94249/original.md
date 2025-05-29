```
upgrades_and_downgrades_consensus(fmp, symbol)
```

Returns consensus upgrades and downgrades for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Upgrades-&-Downgrades-Consensus](https://site.financialmodelingprep.com/developer/docs/#Upgrades-&-Downgrades-Consensus) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the consensus of upgrades and downgrades for AAPL
data = upgrades_and_downgrades_consensus(fmp, AAPL)
```
