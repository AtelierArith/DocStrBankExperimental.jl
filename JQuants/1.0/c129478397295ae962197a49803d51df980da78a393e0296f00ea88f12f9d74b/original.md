```
TradingCalendar(;holidaydivision="", from="", to="")
```

[Trading Calendar API](https://jpx.gitbook.io/j-quants-en/api-reference/trading_calendar)

## Parameters

  * `holidaydivision::AbstractString`: Holiday division. (Non-business day: "0", Business day: "1", Day of TSE Half-Day Trading Sessions: "2", Non-business days with holiday trading: "3")
  * `from::AbstractString`: Start date. (e.g. "2018-01-01")
  * `to::AbstractString`: End date. (e.g. "2018-01-31")

## Examples

```julia
julia> using JQuants

julia> fetch(TradingCalendar(holidaydivision="1", from="2018-01-01", to="2018-01-31"))
```
