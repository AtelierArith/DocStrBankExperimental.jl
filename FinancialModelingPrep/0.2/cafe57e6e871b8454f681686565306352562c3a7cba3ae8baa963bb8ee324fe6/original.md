```
etf_country_weightings(fmp, symbol)
```

Returns the country weightings of a specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: An etf symbol.

See [ETF-Country-Weightings](https://site.financialmodelingprep.com/developer/docs/#ETF-Country-Weightings) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the country weightings of SPY
data = etf_country_weightings(fmp, "SPY")
```
