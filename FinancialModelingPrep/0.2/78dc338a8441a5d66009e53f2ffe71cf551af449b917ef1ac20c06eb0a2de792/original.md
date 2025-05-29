```
financial_ratios(fmp, symbol, params...)
```

Returns common financial ratios for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Financial-Ratios](https://site.financialmodelingprep.com/developer/docs/#Company-Financial-Ratios) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get financial ratios for AAPL in the last 30 quarters
data = financial_ratios(fmp, "AAPL", period = "quarter", limit = 30)
```
