```
stock_split_calendar(fmp, params...)
```

Returns stock split calendar events.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Stock-Split-Calendar](https://site.financialmodelingprep.com/developer/docs/#Stock-Split-Calendar) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the stock split calendar events for Q1 2022
data = stock_split_calendar(fmp, from = "2022-01-01", to = "2022-03-31")
```
