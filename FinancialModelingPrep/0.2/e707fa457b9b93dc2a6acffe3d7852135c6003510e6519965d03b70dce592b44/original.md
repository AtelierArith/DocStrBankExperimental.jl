```
executive_compensation(fmp, symbol)
```

Returns executive compensation for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Executive-Compensation](https://site.financialmodelingprep.com/developer/docs/#Executive-Compensation) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the excecutive compensation for AAPL
data = executive_compensation(fmp, "AAPL")
```
