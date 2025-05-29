```
lwc_panel(charts::LWCChart...; kw...) -> LWCPanel
```

Creates a panel combining several [`charts`](@ref charts).

## Keyword arguments

| Name::Type                             | Default/Possible values                                                  | Description                                                                                                 |
|:-------------------------------------- |:------------------------------------------------------------------------ |:----------------------------------------------------------------------------------------------------------- |
| `x::Int64`                             | `-999`                                                                   | Panel's horizontal coordinates                                                                              |
| `y::Int64`                             | `-999`                                                                   | Panel's vertical coordinates                                                                                |
| `h::Float64`                           | `0.5`                                                                    | Height of the panel as a fraction of the total window height.                                               |
| `name::String`                         | `""`                                                                     | Panel name (will be displayed in the panel header).                                                         |
| `min_y::Union{Real,Nothing}`           | `nothing`                                                                | Lower bound on the y-axis.                                                                                  |
| `left_min_y::Union{Real,Nothing}`      | `nothing`                                                                | Lower bound on the left y-axis.                                                                             |
| `right_min_y::Union{Real,Nothing}`     | `nothing`                                                                | Lower bound on the right y-axis.                                                                            |
| `max_y::Union{Real,Nothing}`           | `nothing`                                                                | Upper bound on the y-axis.                                                                                  |
| `left_max_y::Union{Real,Nothing}`      | `nothing`                                                                | Upper bound on the left y-axis.                                                                             |
| `right_max_y::Union{Real,Nothing}`     | `nothing`                                                                | Upper bound on the right y-axis.                                                                            |
| `seconds_visible::Bool`                | `false`                                                                  | Seconds visibility on the x-axis.                                                                           |
| `bar_spacing::Real`                    | `6`                                                                      | Distance between the stripes in pixels.                                                                     |
| `min_bar_spacing::Real`                | `0.5`                                                                    | Minimum distance between the stripes in pixels.                                                             |
| `tooltip::Bool`                        | true                                                                     | Enables tooltip for points.                                                                                 |
| `tooltip_format::String`               | `"${label_name}: (${time}, ${value})"`                                   | String formatting of tooltip text. Display the variables "title", "time" and "value" in the desired format. |
| `min_charts_for_search`                | `10`                                                                     | Minimum number of charts to search.                                                                         |
| `mode::LWC_PRICE_SCALE_MODE`           | `0`                                                                      | Price scale mode.                                                                                           |
| `crosshair_settings::CrosshairOptions` | `CrosshairOptions()`                                                     | Structure describing crosshair options.                                                                     |
| `cursor::LWC_CURSOR`                   | `LWC_CURSOR_DEFAUL`                                                      | Cursor type.                                                                                                |
| `last_value_visible::Bool`             | `false`                                                                  | Shows the latest price label on the price scale.                                                            |
| `title_visible::Bool`                  | `false`                                                                  | Shows the chart name next to the latest price label.                                                        |
| `legend_mode::LWC_LEGEND_MODE`         | `LWC_LEGEND_LIST_MODE` (`LWC_LEGEND_LIST_MODE`, `LWC_LEGEND_TABLE_MODE`) | Legend box display type.                                                                                    |
| `default_legend_visible::Bool`         | `true`                                                                   | Shows the legend box with data charts names and colors.                                                     |
