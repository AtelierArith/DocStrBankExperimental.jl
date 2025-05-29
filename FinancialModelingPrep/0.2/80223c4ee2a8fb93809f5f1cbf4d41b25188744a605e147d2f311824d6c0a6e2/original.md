```
dowjones_companies(fmp, historical = false)
```

Returns all Dow Jones companies.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `historical::Bool`: Return historical or current companies.

See [List-of-Dow-Jones-Companies](https://site.financialmodelingprep.com/developer/docs/#List-of-Dow-Jones-companies) for more details.
See [Historical-Dow-Jones-Companies](https://site.financialmodelingprep.com/developer/docs/#Historical-Dow-Jones) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all historical Dow Jones companies
data = dowjones_companies(fmp, historical = true)
```
