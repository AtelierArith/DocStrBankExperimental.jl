```
dividend_calendar(fmp, params...)
```

Returns dividend calendar events.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Dividend-Calendar](https://site.financialmodelingprep.com/developer/docs/#Dividend-Calendar) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the dividend calendar events for Q1 2022
data = dividend_calendar(fmp, from = "2022-01-01", to = "2022-03-31")
```
