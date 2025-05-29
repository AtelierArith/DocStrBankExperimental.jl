```
economic_calendar(fmp, params...)
```

Returns economic calendar events.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Economic-Calendar](https://site.financialmodelingprep.com/developer/docs/#Economic-Calendar) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the economic calendar events for Q1 2022
data = economic_calendar(fmp, from = "2022-01-01", to = "2022-03-31")
```
