```
ipo_calendar(fmp, params...)
```

Returns the ipo calendar events.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [IPO-Calendar](https://site.financialmodelingprep.com/developer/docs/#IPO-Calendar) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the ipo calendar events for Q1 2022
data = ipo_calendar(fmp, from = "2022-01-01", to = "2022-03-31")
```
