```
treasury_rates(fmp, params...)
```

Returns the treasury rates for the specified date range.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Treasury-Rates](https://site.financialmodelingprep.com/developer/docs/#Treasury-Rates) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the treasury rates for Q1 2022
data = treasury_rates(fmp, from = "2022-01-01", to = "2022-03-31")
```
