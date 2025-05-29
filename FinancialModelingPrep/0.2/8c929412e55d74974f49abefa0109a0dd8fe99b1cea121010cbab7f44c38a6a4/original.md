```
cash_flow_statements_growth(fmp, symbol, params...)
```

Returns cash flow statements growth for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Cash-Flow-Statements-Growth](https://site.financialmodelingprep.com/developer/docs/#Financial-Statements-Growth) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the last 5 annual statements growth for AAPL
data = cash_flow_statements_growth(fmp, "AAPL", limit = 5)
```
