```
TradingCalendar(;holidaydivision="", from="", to="")
```

[Trading Calendar API](https://jpx.gitbook.io/j-quants-en/api-reference/trading_calendar)

## パラメータ

  * `holidaydivision::AbstractString`: 休日区分。 (非営業日: "0", 営業日: "1", TSEの半日取引セッションの日: "2", 休日取引のある非営業日: "3")
  * `from::AbstractString`: 開始日。 (例: "2018-01-01")
  * `to::AbstractString`: 終了日。 (例: "2018-01-31")

## 例

```julia
julia> using JQuants

julia> fetch(TradingCalendar(holidaydivision="1", from="2018-01-01", to="2018-01-31"))
```
