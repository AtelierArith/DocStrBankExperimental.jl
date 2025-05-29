```
institutional_positions(fmp, symbol, params...)
```

Returns institutional positions for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Institutional-Stock-Ownership](https://site.financialmodelingprep.com/developer/docs/#Institutional-Stock-Ownership) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the institutional positions for AAPL including the current quarter
data = institutional_positions(fmp, "AAPL", includeCurrentQuarter = true)
```
