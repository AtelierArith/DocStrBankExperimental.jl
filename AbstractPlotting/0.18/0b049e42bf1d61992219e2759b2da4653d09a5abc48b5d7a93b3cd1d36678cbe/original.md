```
DataInspector(figure; kwargs...)
```

Creates a data inspector which will show relevant information in a tooltip  when you hover over a plot. If you wish to exclude a plot you may set  `plot.inspectable[] = false`. 

### Keyword Arguments:

  * `range = 10`: Controls the snapping range for selecting an element of a plot.
  * `enabled = true`: Disables inspection of plots when set to false. Can also be   adjusted with `enable!(inspector)` and `disable!(inspector)`.
  * `text_padding = Vec4f0(5, 5, 3, 3)`: Padding for the box drawn around the    tooltip text. (left, right, bottom, top)
  * `text_align = (:left, :bottom)`: Alignment of text within the tooltip. This    does not affect the alignment of the tooltip relative to the cursor.
  * `textcolor = :black`: Tooltip text color.
  * `textsize = 20`: Tooltip text size.
  * `font = "Dejavu Sans"`: Tooltip font.
  * `background_color = :white`: Background color of the tooltip.
  * `outline_color = :grey`: Outline color of the tooltip.
  * `outline_linestyle = nothing`: Linestyle of the tooltip outline.
  * `outline_linewidth = 2`: Linewidth of the tooltip outline.
  * `indicator_color = :red`: Color of the selection indicator.
  * `indicator_linewidth = 2`: Linewidth of the selection indicator.
  * `indicator_linestyle = nothing`: Linestyle of the selection indicator
  * `tooltip_align = (:center, :top)`: Default position of the tooltip relative to   the cursor or current selection. The real align may adjust to keep the    tooltip in view.
  * `tooltip_offset = Vec2f0(20)`: Offset from the indicator to the tooltip.
  * `depth = 9e3`: Depth value of the tooltip. This should be high so that the    tooltip is always in front.
  * `priority = 100`: The priority of creating a tooltip on a mouse movement or    scrolling event.
