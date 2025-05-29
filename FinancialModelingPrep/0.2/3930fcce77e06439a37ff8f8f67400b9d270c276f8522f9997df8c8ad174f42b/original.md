```
etf_holders(fmp, symbol)
```

Returns the etf holders of a specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: An etf symbol.

See [ETF-Holders](https://site.financialmodelingprep.com/developer/docs/#ETF-Holders) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the etf holders for SPY
data = etf_holders(fmp, "SPY")
```
