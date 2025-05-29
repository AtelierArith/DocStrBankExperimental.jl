```
ipo_calendar_confirmed(fmp, params...)
```

Returns the confirmed ipo calendar events.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [IPO-Calendar-Confirmed](https://site.financialmodelingprep.com/developer/docs/#IPO-calendar-Confirmed) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the confirmed ipo calendar events for Q1 2022
data = ipo_calendar_confirmed(fmp, from = "2022-01-01", to = "2022-03-31")
```
