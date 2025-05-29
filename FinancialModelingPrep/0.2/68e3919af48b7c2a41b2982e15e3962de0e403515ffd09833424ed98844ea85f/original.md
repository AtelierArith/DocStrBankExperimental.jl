```
company_notes(fmp, symbol)
```

Returns notes due for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Company-Notes-Due](https://site.financialmodelingprep.com/developer/docs/#Company-Notes-due) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all notes due for AAPL
data = company_notes(fmp, "AAPL")
```
