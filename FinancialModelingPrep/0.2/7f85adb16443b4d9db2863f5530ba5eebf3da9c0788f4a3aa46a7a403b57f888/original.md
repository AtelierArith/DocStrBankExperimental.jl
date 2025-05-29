```
key_metrics(fmp, symbol, period, params...)
```

Returns key metrics for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `period::String`: A `REPORTING_PERIODS` option.
  * `params...`: Additional keyword query params.

See [Key-Metrics](https://site.financialmodelingprep.com/developer/docs/#Company-Key-Metrics) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get key metrics for AAPL in the last 30 years by ttm
data = key_metrics(fmp, "AAPL", period = REPORTING_PERIODS.ttm, limit = 30)
```
