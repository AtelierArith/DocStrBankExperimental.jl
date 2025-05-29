```
sp500_companies(fmp, historical = false)
```

Returns all S&P 500 companies.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `historical::Bool`: Return historical or current companies.

See [List-of-S&P-500-Companies](https://site.financialmodelingprep.com/developer/docs/#List-of-S&P-500-companies) for more details.
See [Historical-S&P-500-Companies](https://site.financialmodelingprep.com/developer/docs/#Historical-S&P-500) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all historical S&P 500 companies
data = sp500_companies(fmp, historical = true)
```
