```
lwc_candlestick(data::Vector{LWCCandleChartItem}; kw...) -> LWCChart
```

Creates a [`LWCChart`](@ref) object that contains candlesticks chart information. A general method that allows you to customize each chart node using [`LWCCandleChartItem`](@ref).

Wrapper function for [`Candlestick`](https://tradingview.github.io/lightweight-charts/docs/series-types#candlestick).

## Keyword arguments

| Name::Type                           | Default (Possible values) | Description                                 |
|:------------------------------------ |:------------------------- |:------------------------------------------- |
| `price_scale_id::LWC_PRICE_SCALE_ID` | `LWC_LEFT` (`LWC_RIGHT`)  | Y-axis display side.                        |
| `label_name::String`                 | `""`                      | Chart name.                                 |
| `visible::Bool`                      | `true`                    | Chart visibility.                           |
| `precision::Int64`                   | `2`                       | Number of decimal places for y-axis values. |
| `up_color::String`                   | `"#26a69a"`               | Color of bullish candle (increasing).       |
| `down_color::String`                 | `"#ef5350"`               | Color of bearish candle (decreasing).       |
| `wick_visible::Bool`                 | `true`                    | Wick visibility.                            |
| `border_visible::Bool`               | `true`                    | Candle borders visibility.                  |
| `border_color::String`               | `"#378658"`               | Candle border color.                        |
| `border_up_color::String`            | `"#26a69a"`               | Boder color of bullish candle.              |
| `border_down_color::String`          | `"#ef5350"`               | Boder color of bearish candle.              |
| `wick_color::String`                 | `"#737375"`               | Wick color.                                 |
| `wick_up_color::String`              | `"#26a69a"`               | Wick color of bullish candle.               |
| `wick_down_color::String`            | `"#ef5350"`               | Wick color of bearish candle.               |
| `plugins::Vector{LWCPlugin}`         | `LWCPlugin[]`             | Additional plugins.                         |
