```
crowdfunding_offerings(fmp, cik)
```

Returns the crowdfunding offerings for the specified CIK.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `cik::String`: A CIK.

See [Crowdfunding-Offerings-by-CIK](https://site.financialmodelingprep.com/developer/docs/#Crowdfunding-Offerings-by-CIK) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the crowdfundings offerings for OYO Fitness
data = crowdfunding_offerings(fmp, cik = "0001916078")
```
