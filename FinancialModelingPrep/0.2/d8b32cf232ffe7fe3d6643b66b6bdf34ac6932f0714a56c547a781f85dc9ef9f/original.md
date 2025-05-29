```
insider_roster_statistics(fmp, symbol)
```

Returns insider roster statistics for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Insider-Roster-Statistics](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the insider roster statistics for AAPL
data = insider_roster_statistics(fmp, "AAPL")
```
