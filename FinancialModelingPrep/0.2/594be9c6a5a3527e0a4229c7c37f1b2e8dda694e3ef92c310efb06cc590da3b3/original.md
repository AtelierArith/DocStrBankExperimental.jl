```
nyse_schedule(fmp)
```

Returns a JSON dictionary of the NYSE schedule including market hours and market holidays.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [NYSE-Schedule](https://site.financialmodelingprep.com/developer/docs/#NYSE-Holidays-and-Trading-Hours) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the NYSE holiday schedule
data = nyse_schedule(fmp)[:stockMarketHolidays]
```
