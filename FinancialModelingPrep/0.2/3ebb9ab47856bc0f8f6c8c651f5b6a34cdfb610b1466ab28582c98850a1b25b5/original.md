```
technical_indicators(fmp, symbol, frequency = TIME_FREQUENCIES.daily, period = 200, type = "SMA")
```

Returns the historical price quote for the specified symbol and frequency.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `frequency::String`: A time frequency.
  * `period::Integer`: The indicator period.
  * `type::String`: The indicator type.

See [Daily-Indicators](https://site.financialmodelingprep.com/developer/docs/#Daily-Indicators) for more details.
See [Intraday-Indicators](https://site.financialmodelingprep.com/developer/docs/#Intraday-Indicators) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the daily 50 period SMA for AAPL
data = technical_indicators(fmp, "AAPL", period = 50)

# get the 15m 10 period WMA for AAPL
data = technical_indicators(fmp, "AAPL", TIME_FREQUENCIES.minutes15, period = 10, type = "wma")
```
