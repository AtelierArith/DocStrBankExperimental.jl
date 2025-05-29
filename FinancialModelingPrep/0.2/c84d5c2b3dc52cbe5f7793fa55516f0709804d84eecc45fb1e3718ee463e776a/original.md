```
equity_offerings(fmp, cik)
```

Returns the crowdfunding offerings for the specified CIK.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `cik::String`: A CIK.

See [Equity-Offerings-Fundraising-by-CIK](https://site.financialmodelingprep.com/developer/docs/#Equity-offerings-Fundraising-by-CIK) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the equity offerings for Marinalife
data = equity_offerings(fmp, cik = "0001870523")
```
