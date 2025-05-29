```
price_history(ticker; kwargs...)
```

Get price history of a given ticker, everything but `ticker` have default value specified by TD api:  https://developer.tdameritrade.com/price-history/apis/get/marketdata/{symbol}/pricehistory

# Optional kwargs:

periodType period frequencyType frequency endDate startDate needExtendedHoursData

# Examples

```julia
using Dates

price_history("GE", Minute(1), Day(1)) #a tick = a day for the past day
price_history("GE", Day(1), Year(2)) #a tick = a day for the past 2 years
price_history("AAPL", Day(1), now()-Day(1), now())
```
