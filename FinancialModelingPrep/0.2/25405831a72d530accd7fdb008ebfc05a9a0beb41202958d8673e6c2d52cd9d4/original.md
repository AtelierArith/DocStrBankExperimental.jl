```
price_targets_by_company(fmp, company)
```

Returns price targets from the specified company.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * company::String: An analyst company name.

See [Price-Target-by-Analyst-Company](https://site.financialmodelingprep.com/developer/docs/#Price-Target-by-Analyst-Company) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the price targets from Barclays
data = price_targets_by_company(fmp, company = "Barclays")
```
