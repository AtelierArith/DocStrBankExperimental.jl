```
LWCSimpleChartItem(time::Int64, value::Real; kw...)
LWCSimpleChartItem(time::TimeType, value::Real; kw...)
```

This data type allows you to customize the colors for each point of your chart. Supported for [`lwc_line`](@ref), [`lwc_area`](@ref), [`lwc_baseline`](@ref) and [`lwc_histogram`](@ref) methods.

## Fields

  * `time::Int64`: Data unix time.
  * `value::Float64`: Data value.

## Keyword arguments

| Name::Type                    | Default (Possible values) | Description          |
|:----------------------------- |:------------------------- |:-------------------- |
| `line_color::String`          | `nothing`                 | Line color.          |
| `top_color::String`           | `nothing`                 | Top color.           |
| `bottom_color::String`        | `nothing`                 | Bottom color.        |
| `top_fill_color_1::String`    | `nothing`                 | Top fill color 1.    |
| `top_fill_color_2::String`    | `nothing`                 | Top fill color 2.    |
| `top_line_color::String`      | `nothing`                 | Top line color.      |
| `bottom_fill_color_1::String` | `nothing`                 | Bottom fill color 1. |
| `bottom_fill_color_2::String` | `nothing`                 | Bottom fill color 2. |
| `bottom_line_color::String`   | `nothing`                 | Bottom line color.   |
| `color::String`               | `nothing`                 | Color.               |
