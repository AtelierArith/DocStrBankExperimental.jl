```
etf_sector_weightings(fmp, symbol)
```

Returns the sector weightings of a specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: An etf symbol.

See [ETF-Sector-Weightings](https://site.financialmodelingprep.com/developer/docs/#ETF-Sector-Weightings) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the sector weightings of SPY
data = etf_sector_weightings(fmp, "SPY")
```
