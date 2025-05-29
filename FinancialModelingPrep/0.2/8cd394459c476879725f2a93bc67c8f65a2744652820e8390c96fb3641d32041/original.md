```
balance_sheet_statements(fmp, symbol, reported = false, params...)
```

Returns balance sheet statements for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `reported::Bool`: Return the reported or normalized statements.
  * `params...`: Additional keyword query params.

See [Balance-Sheet-Statements](https://site.financialmodelingprep.com/developer/docs#Company-Financial-Statements) for more details.
See [Balance-Sheet-Statements-As-Reported](https://site.financialmodelingprep.com/developer/docs#Company-Financial-Statements-As-Reported) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the last 10 quarterly statments for AAPL
data = balance_sheet_statements(fmp, "AAPL", period = "quarter", limit = 10)

# get the last 5 annual statements as reported for AAPL
data = balance_sheet_statements(fmp, "AAPL", reported = true, limit = 5)
```
