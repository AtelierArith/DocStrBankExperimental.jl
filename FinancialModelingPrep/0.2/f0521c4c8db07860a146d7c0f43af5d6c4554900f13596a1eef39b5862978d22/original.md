```
earnings_surprises(fmp, symbol)
```

Returns earnings suprises for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Earnings-Surprises](https://site.financialmodelingprep.com/developer/docs/#Earnings-Surprises) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the latest earnings surprises for AAPL
data = earnings_surprises(fmp, "AAPL")
```
