```
institutional_ownership_weightings(fmp, symbol, params...)
```

Returns institutional ownership weightings for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Institutional-Stock-by-Shares-Held-and-Date](https://site.financialmodelingprep.com/developer/docs/#Institutional-Ownership-by-Shares-Held-and-Date) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the institutional ownership weightings for AAPL in Q3 of 2021
data = institutional_ownership_weightings(fmp, "AAPL", date = "2021-09-30")
```
