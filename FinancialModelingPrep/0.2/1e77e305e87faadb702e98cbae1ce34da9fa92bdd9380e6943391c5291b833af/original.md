```
company_profile(fmp, symbol)
```

Returns the company profile for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Company-Profile](https://site.financialmodelingprep.com/developer/docs/#Company-Profile) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the company profile for AAPL
data = company_profile(fmp, "AAPL")
```
