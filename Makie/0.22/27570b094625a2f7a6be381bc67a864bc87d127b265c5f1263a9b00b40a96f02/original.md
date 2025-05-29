```
DataInspector(figure_axis_or_scene = current_figure(); kwargs...)
```

Creates a data inspector which will show relevant information in a tooltip when you hover over a plot.

This functionality can be disabled on a per-plot basis by setting `plot.inspectable[] = false`. The displayed text can be adjusted by setting `plot.inspector_label` to a function `(plot, index, position) -> "my_label"` returning a label. See Makie documentation for more detail.

### Keyword Arguments:

  * `range = 10`: Controls the snapping range for selecting an element of a plot.
  * `priority = 100`: The priority of creating a tooltip on a mouse movement or   scrolling event.
  * `enabled = true`: Disables inspection of plots when set to false. Can also be   adjusted with `enable!(inspector)` and `disable!(inspector)`.
  * `indicator_color = :red`: Color of the selection indicator.
  * `indicator_linewidth = 2`: Linewidth of the selection indicator.
  * `indicator_linestyle = nothing`: Linestyle of the selection indicator
  * `enable_indicators = true`: Enables or disables indicators
  * `depth = 9e3`: Depth value of the tooltip. This should be high so that the   tooltip is always in front.
  * `apply_tooltip_offset = true`: Enables or disables offsetting tooltips based   on, for example, markersize.
  * and all attributes from `Tooltip`
