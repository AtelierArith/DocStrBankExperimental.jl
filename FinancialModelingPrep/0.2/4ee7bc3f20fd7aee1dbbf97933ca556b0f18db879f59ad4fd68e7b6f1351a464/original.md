```
historical_price_quote(fmp, symbol, frequency = TIME_FREQUENCIES.daily, params...)
```

Returns a JSON table with the historical price quote for the specified symbol and frequency.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `frequency::String`: A time frame.
  * `params...`: Additional keyword query params.

See [Historical-Stock-Quote](https://site.financialmodelingprep.com/developer/docs/#Stock-Historical-Price) for more details.
See [Historical-Index-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-stock-index-prices) for more details.
See [Historical-Euronext-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-EuroNext-prices) for more details.
See [Historical-TSX-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-TSX-prices) for more details.
See [Historical-Cryptocurrencies-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-Cryptocurrencies-Price) for more details.
See [Historical-Forex-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-Forex-Price) for more details.
See [Historical-Commodities-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-commodities-prices) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the 15m historical price quote for AAPL
data = historical_price_quote(fmp, "AAPL", frequency = TIME_FREQUENCIES.minutes15)

# get the 4hr historical price quote for BTCUSD
data = historical_price_quote(fmp, "BTCUSD", frequency = TIME_FREQUENCIES.hours4)

# get the daily historical price quote time series for EURUSD
data = historical_price_quote(fmp, "EURUSD", frequency = TIME_FREQUENCIES.daily, timeseries = 5)
```
