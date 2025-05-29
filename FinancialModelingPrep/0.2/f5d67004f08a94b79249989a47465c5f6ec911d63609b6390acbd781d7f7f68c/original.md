```
company_outlook(fmp, symbol, accessor)
```

Returns a JSON table or dictionary of the company outlook for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `accessor::Symbol`: An accessor Symbol which contains a nested array.

See [Company-Outlook](https://site.financialmodelingprep.com/developer/docs/#Company-Outlook) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the company outlook for AAPL
data = company_outlook(fmp, "AAPL")
```
