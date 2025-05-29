```
mutual_fund_search(fmp, name)
```

Returns all mutual funds matching the specified name.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `name::String`: An institution name.

See [Mutual-Fund-Holdings-Search](https://site.financialmodelingprep.com/developer/docs/#Mutual-fund-holdings-search) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all mutual funds from Vanguard
data = mutual_fund_search(fmp, name = "Vanguard")
```
