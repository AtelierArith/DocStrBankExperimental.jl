```
company_from_cik(fmp, cik)
```

Returns all company names matching the specified CIK.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `cik::String`: A CIK.

See [CIK-Mapper](https://site.financialmodelingprep.com/developer/docs/#Form-13F) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the company name matching the CIK
data = company_from_cik(fmp, cik = "0001067983")
```
