```
market_hours(market::AbstractString, date=today())
market_hours(market::Array, date=today())
```

将来の市場の営業時間を取得する: https://developer.tdameritrade.com/market-hours/apis/get/marketdata/%7Bmarket%7D/hours

複数の市場の営業時間を取得する: https://developer.tdameritrade.com/market-hours/apis/get/marketdata/hours

`market` は単一の `String` または `Array` または複数の `String` であることができます。

# 例

```julia
market_hours("OPTION", "2020-08-08")
market_hours(["OPTION", "FUTURE", "EQUITY"], today() + Day(1))
```
