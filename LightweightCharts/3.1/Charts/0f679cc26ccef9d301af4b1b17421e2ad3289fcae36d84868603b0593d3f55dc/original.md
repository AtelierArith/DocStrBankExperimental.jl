```
lwc_bar(data::Vector{LWCCandleChartItem}; kw...) -> LWCChart
```

Creates a [`LWCChart`](@ref) object that contains bar chart information. A general method that allows you to customize each chart node using [`LWCCandleChartItem`](@ref).

Wrapper function for [`Bar`](https://tradingview.github.io/lightweight-charts/docs/series-types#bar).

## Keyword arguments

| Name::Type                           | Default (Possible values) | Description                                 |
|:------------------------------------ |:------------------------- |:------------------------------------------- |
| `price_scale_id::LWC_PRICE_SCALE_ID` | `LWC_LEFT` (`LWC_RIGHT`)  | Y-axis display side.                        |
| `label_name::String`                 | `""`                      | Chart name.                                 |
| `visible::Bool`                      | `true`                    | Chart visibility.                           |
| `precision::Int64`                   | `2`                       | Number of decimal places for y-axis values. |
| `up_color::String`                   | `"#26a69a"`               | Color of bullish candle (increasing).       |
| `down_color::String`                 | `"#ef5350"`               | Color of bearish candle (decreasing).       |
| `open_visible::Bool`                 | `true`                    | Open tick visibility.                       |
| `thin_bars::Bool`                    | `true`                    | Thin bars.                                  |
| `plugins::Vector{LWCPlugin}`         | `LWCPlugin[]`             | Additional plugins.                         |
