```
survivorship_bias(fmp, symbol, date)
```

Returns a JSON dictionary of the survivorship bias for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `date::String`: A yyyy-mm-dd formatted date string.

See [Survivorship-Bias](https://site.financialmodelingprep.com/developer/docs/#Survivorship-Bias-Free-EOD) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the survivorship bias for AAPL to Jan 3, 2012
data = survivorship_bias(fmp, "AAPL", date = "2012-01-03")
```
