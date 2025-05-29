```
insider_roster(fmp, symbol)
```

Returns a JSON table with the insider roster for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Insider-Roster](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the insider roster for AAPL
data = insider_roster(fmp, "AAPL")
```
