```
nasdaq_companies(fmp, historical = false)
```

Returns all Nasdaq companies.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `historical::Bool`: Return historical or current companies.

See [List-of-Nasdaq-100-Companies](https://site.financialmodelingprep.com/developer/docs/#List-of-Nasdaq-100-companies) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all historical Nasdaq 100 companies
data = nasdaq_companies(fmp, historical = true)
```
