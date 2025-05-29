```
lwc_histogram(Vector{LWCSimpleChartItem}; kw...) -> LWCChart
```

Creates a [`LWCChart`](@ref) object that contains line chart information. A general method that allows you to customize each chart node using [`LWCSimpleChartItem`](@ref).

Wrapper function for [`Histogram`](https://tradingview.github.io/lightweight-charts/docs/series-types#histogram).

## Keyword arguments

| Name::Type                           | Default (Possible values) | Description                                                                         |
|:------------------------------------ |:------------------------- |:----------------------------------------------------------------------------------- |
| `price_scale_id::LWC_PRICE_SCALE_ID` | `LWC_LEFT` (`LWC_RIGHT`)  | Y-axis display side.                                                                |
| `label_name::String`                 | `""`                      | Chart name.                                                                         |
| `visible::Bool`                      | `true`                    | Chart visibility.                                                                   |
| `precision::Int64`                   | `2`                       | Number of decimal places for y-axis values.                                         |
| `color::String`                      | Random color              | Histogram color.                                                                    |
| `base::Real`                         | `0.0`                     | The value relative to which the larger or smaller histogram values will be located. |
| `plugins::Vector{LWCPlugin}`         | `LWCPlugin[]`             | Additional plugins.                                                                 |
