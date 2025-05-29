```
crowdfunding_offerings_search(fmp, name)
```

Returns crowfunding offering dates for the specified name.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `name::String`: A company name.

See [Crowdfunding-Offerings-Company-Search](https://site.financialmodelingprep.com/developer/docs/#Crowdfunding-Offerings-Company-Search) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the crowdfunding offering dates for Enotap
data = crowdfunding_offerings_search(fmp, name = "Enotap")
```
