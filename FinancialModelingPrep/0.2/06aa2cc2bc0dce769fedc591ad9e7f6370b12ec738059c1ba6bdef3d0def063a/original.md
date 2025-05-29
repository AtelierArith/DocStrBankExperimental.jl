```
historical_earnings_calendar(fmp, symbol, params...)
```

Returns historical earnings calendar events.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Earnings-Calendar](https://site.financialmodelingprep.com/developer/docs/#Earnings-Calendar) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the last 50 earnings calendar events for AAPL
data = historical_earnings_calendar(fmp, "AAPL", limit = 50)
```
