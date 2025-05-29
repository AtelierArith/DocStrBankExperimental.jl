```
LWCCandleChartItem(time::Int64, open::Real, high::Real, low::Real, close::Real; kw...)
LWCCandleChartItem(time::TimeType, open::Real, high::Real, low::Real, close::Real; kw...)
```

Representation of candlestick data for [`lwc_candlestick`](@ref) and [`lwc_bar`](@ref) methods.

## Fields

  * `time::Int64`
  * `open::Float64`
  * `high::Float64`
  * `low::Float64`
  * `close::Float64`

## Keyword arguments

| Name::Type             | Default (Possible values) | Description   |
|:---------------------- |:------------------------- |:------------- |
| `color::String`        | `nothing`                 | Candle color. |
| `border_color::String` | `nothing`                 | Border color. |
| `wick_color::String`   | `nothing`                 | Wick color.   |
