```
market_hours(market::AbstractString, date=today())
market_hours(market::Array, date=today())
```

Get hours of a market in the future: https://developer.tdameritrade.com/market-hours/apis/get/marketdata/%7Bmarket%7D/hours

Get hours of multiple markets: https://developer.tdameritrade.com/market-hours/apis/get/marketdata/hours

`market` can be a single `String` or an `Array` or multiple `String`s

# Examples

```julia
market_hours("OPTION", "2020-08-08")
market_hours(["OPTION", "FUTURE", "EQUITY"], today() + Day(1))
```
