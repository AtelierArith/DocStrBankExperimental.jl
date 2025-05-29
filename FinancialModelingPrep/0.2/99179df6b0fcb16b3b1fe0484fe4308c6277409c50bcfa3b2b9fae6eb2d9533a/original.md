```
financial_statements(fmp, symbol, params...)
```

Returns financial statements as reported for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Full-Financial-Statements-As-Reported](https://site.financialmodelingprep.com/developer/docs#Company-Financial-Statements-As-Reported) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all quarterly statements as reported for AAPL
data = financial_statements(fmp, "AAPL", period = "quarter")
```
