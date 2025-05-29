```
historical_sector_performances(fmp, params...)
```

Returns historical sector perfromances.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Sectors-Performance](https://site.financialmodelingprep.com/developer/docs/#Stock-Market-Sectors-Performance) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the 10 most recent historical sector performances
data = historical_sector_performances(fmp, limit = 10)
```
