```
forms_13f(fmp, cik, date)
```

Returns all form 13F filing matching the specified CIK and date.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `cik::String`: A CIK.
  * `date::String`: A yyyy-mm-dd formatted date string.

See [Form-13F](https://site.financialmodelingprep.com/developer/docs/#Form-13F) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all form 13F form for the CIK on June 30, 2022.
data = forms_13f(fmp, cik = "0001067983", date = "2022-06-30")
```
