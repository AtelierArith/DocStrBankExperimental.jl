```
upgrades_and_downgrades_by_company(fmp, company)
```

Returns upgrades and downgrades for the specified company.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Upgrades-&-Downgrades-By-Company](https://site.financialmodelingprep.com/developer/docs/#Upgrades-&-Downgrades-By-Company) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the consensus of upgrades and downgrades for Barclays
data = upgrades_and_downgrades_by_company(fmp, company = "Barclays")
```
