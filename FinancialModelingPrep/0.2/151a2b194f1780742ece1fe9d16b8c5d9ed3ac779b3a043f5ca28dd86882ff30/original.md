```
earnings_calendar(fmp, params...)
```

Returns earnings calendar events.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Earnings-Calendar](https://site.financialmodelingprep.com/developer/docs/#Earnings-Calendar) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the earnings calendar events for Q1 2022
data = earnings_calendar(fmp, from = "2022-01-01", to = "2022-03-31")
```
