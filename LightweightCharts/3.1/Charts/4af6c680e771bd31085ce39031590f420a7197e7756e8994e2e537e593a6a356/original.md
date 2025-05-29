```
lwc_line(Vector{LWCSimpleChartItem}; kw...) -> LWCChart
```

Creates a [`LWCChart`](@ref) object that contains line chart information. A general method that allows you to customize each chart node using [`LWCSimpleChartItem`](@ref).

Wrapper function for [`Line`](https://tradingview.github.io/lightweight-charts/docs/series-types#line).

## Keyword arguments

| Name::Type                                  | Default (Possible values)                                                         | Description                                 |
|:------------------------------------------- |:--------------------------------------------------------------------------------- |:------------------------------------------- |
| `price_scale_id::LWC_PRICE_SCALE_ID`        | `LWC_LEFT` (`LWC_RIGHT`)                                                          | Y-axis display side.                        |
| `label_name::String`                        | `""`                                                                              | Chart name.                                 |
| `visible::Bool`                             | `true`                                                                            | Chart visibility.                           |
| `precision::Int64`                          | `2`                                                                               | Number of decimal places for y-axis values. |
| `line_color::String`                        | Random color                                                                      | Line color.                                 |
| `line_style::LWC_LINE_STYLES`               | `LWC_SOLID` (`LWC_DOTTED`, `LWC_DASHED`, `LWC_LARGE_DASHED`, `LWC_SPARSE_DOTTED`) | Line style.                                 |
| `line_width::Int64`                         | `1`                                                                               | Line width.                                 |
| `line_type::LWC_LINE_TYPES`                 | `LWC_SIMPLE` (`LWC_STEP`, `LWC_CURVED`)                                           | Line type.                                  |
| `line_visible::Bool`                        | `true`                                                                            | Line visibility.                            |
| `point_markers_visible::Bool`               | `false`                                                                           | Displaying markers on line nodes.           |
| `point_markers_radius::Float64`             | `4.0`                                                                             | Size of markers.                            |
| `crosshair_marker_visible::Bool`            | `true`                                                                            | Cursor crosshair visibility.                |
| `crosshair_marker_radius::Float64`          | `4.0`                                                                             | Size of crosshair.                          |
| `crosshair_marker_border_color::String`     | `"#758696"`                                                                       | Border color of crosshair.                  |
| `crosshair_marker_background_color::String` | `"#4c525e"`                                                                       | Background color of crosshair.              |
| `crosshair_marker_border_width::Float64`    | `2.0`                                                                             | Border width of the crosshair.              |
| `plugins::Vector{LWCPlugin}`                | `LWCPlugin[]`                                                                     | Additional plugins.                         |
