```
financial_statements_growth(fmp, symbol, params...)
```

Returns financial statements growth for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Financial-Statements-Growth](https://site.financialmodelingprep.com/developer/docs/#Company-Financial-Growth) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the last 5 annual statements growth for AAPL
data = financial_statements_growth(fmp, "AAPL", limit = 5)
```
