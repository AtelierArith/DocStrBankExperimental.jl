```
ipo_calendar_prospectus(fmp, params...)
```

Returns the ipo calendar events with prospectus.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [IPO-Calendar-with-Prospectus](https://site.financialmodelingprep.com/developer/docs/#IPO-calendar-with-prospectus) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the ipo calendar events with prospectus for Q1 2022
data = ipo_calendar_prospectus(fmp, from = "2022-01-01", to = "2022-03-31")
```
