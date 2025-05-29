```
filing_dates(fmp, cik)
```

Returns all form 13F filing dates matching the specified CIK.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `cik::String`: A CIK.

See [Form-13F-Filing-Dates](https://site.financialmodelingprep.com/developer/docs/#Form-13F) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all form 13F filing dates matching the CIK
data = filing_dates(fmp, cik = "0001067983")
```
