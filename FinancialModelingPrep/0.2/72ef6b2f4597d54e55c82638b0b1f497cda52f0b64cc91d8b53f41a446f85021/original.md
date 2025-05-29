```
etf_exposure(fmp, symbol)
```

Returns the etf exposure for a specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [ETF-Stock-Exposure](https://site.financialmodelingprep.com/developer/docs/#ETF-Stock-Exposure) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the etf exposure for AAPL
data = etf_exposure(fmp, "AAPL")
```
