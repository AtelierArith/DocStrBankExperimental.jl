The main plot command. Use `plot` to create a new plot object, and `plot!` to add to an existing one:

```
    plot(args...; kw...)                  # creates a new plot window, and sets it to be the current
    plot!(args...; kw...)                 # adds to the `current`
    plot!(plotobj, args...; kw...)        # adds to the plot `plotobj`
```

There are lots of ways to pass in data, and lots of keyword arguments... just try it and it will likely work as expected. When you pass in matrices, it splits by columns. To see the list of available attributes, use the `plotattr(attr)` function, where `attr` is the symbol `:Series`, `:Subplot`, `:Plot`, or `:Axis`. Pass any attribute to `plotattr` as a String to look up its docstring, e.g., `plotattr("seriestype")`.

# Extended help

## Series attributes

  * arrow
  * bar_edges
  * bar_position
  * bar_width
  * bins
  * colorbar_entry
  * connections
  * contour_labels
  * contours
  * extra_kwargs
  * fill
  * fill_z
  * fillalpha
  * fillcolor
  * fillrange
  * fillstyle
  * group
  * hover
  * label
  * levels
  * line
  * line_z
  * linealpha
  * linecolor
  * linestyle
  * linewidth
  * marker
  * marker_z
  * markeralpha
  * markercolor
  * markershape
  * markersize
  * markerstrokealpha
  * markerstrokecolor
  * markerstrokestyle
  * markerstrokewidth
  * normalize
  * orientation
  * permute
  * primary
  * quiver
  * ribbon
  * series_annotations
  * seriesalpha
  * seriescolor
  * seriestype
  * show_empty_bins
  * smooth
  * stride
  * subplot
  * weights
  * x
  * xerror
  * y
  * yerror
  * z
  * z_order
  * zerror

## Axis attributes

Prepend these with the axis letter (x, y or z)

  * axis
  * discrete_values
  * draw_arrow
  * flip
  * foreground_color_axis
  * foreground_color_border
  * foreground_color_grid
  * foreground_color_guide
  * foreground_color_minor_grid
  * foreground_color_text
  * formatter
  * grid
  * gridalpha
  * gridlinewidth
  * gridstyle
  * guide
  * guide_position
  * guidefont
  * guidefontcolor
  * guidefontfamily
  * guidefonthalign
  * guidefontrotation
  * guidefontsize
  * guidefontvalign
  * lims
  * link
  * minorgrid
  * minorgridalpha
  * minorgridlinewidth
  * minorgridstyle
  * minorticks
  * mirror
  * rotation
  * scale
  * showaxis
  * tick_direction
  * tickfont
  * tickfontcolor
  * tickfontfamily
  * tickfonthalign
  * tickfontrotation
  * tickfontsize
  * tickfontvalign
  * ticks
  * unitformat
  * widen

## Subplot attributes

  * annotationcolor
  * annotationfontfamily
  * annotationfontsize
  * annotationhalign
  * annotationrotation
  * annotations
  * annotationvalign
  * aspect_ratio
  * background_color_inside
  * background_color_subplot
  * bottom_margin
  * camera
  * clims
  * color_palette
  * colorbar
  * colorbar_continuous_values
  * colorbar_discrete_values
  * colorbar_fontfamily
  * colorbar_formatter
  * colorbar_scale
  * colorbar_tickfontcolor
  * colorbar_tickfontfamily
  * colorbar_tickfonthalign
  * colorbar_tickfontrotation
  * colorbar_tickfontsize
  * colorbar_tickfontvalign
  * colorbar_ticks
  * colorbar_title
  * colorbar_title_location
  * colorbar_titlefont
  * colorbar_titlefontcolor
  * colorbar_titlefontfamily
  * colorbar_titlefonthalign
  * colorbar_titlefontrotation
  * colorbar_titlefontsize
  * colorbar_titlefontvalign
  * extra_kwargs
  * fontfamily_subplot
  * foreground_color_subplot
  * foreground_color_title
  * framestyle
  * left_margin
  * legend_background_color
  * legend_column
  * legend_font
  * legend_font_color
  * legend_font_family
  * legend_font_halign
  * legend_font_pointsize
  * legend_font_rotation
  * legend_font_valign
  * legend_foreground_color
  * legend_position
  * legend_title
  * legend_title_font
  * legend_title_font_color
  * legend_title_font_family
  * legend_title_font_halign
  * legend_title_font_pointsize
  * legend_title_font_rotation
  * legend_title_font_valign
  * margin
  * plot_title_font
  * projection
  * projection_type
  * right_margin
  * subplot_index
  * title
  * title_font
  * titlefontcolor
  * titlefontfamily
  * titlefonthalign
  * titlefontrotation
  * titlefontsize
  * titlefontvalign
  * titlelocation
  * top_margin

## Plot attributes

  * background_color
  * background_color_outside
  * display_type
  * dpi
  * extra_kwargs
  * extra_plot_kwargs
  * fontfamily
  * foreground_color
  * html_output_format
  * inset_subplots
  * layout
  * link
  * overwrite_figure
  * plot_title
  * plot_titlefontcolor
  * plot_titlefontfamily
  * plot_titlefonthalign
  * plot_titlefontrotation
  * plot_titlefontsize
  * plot_titlefontvalign
  * plot_titleindex
  * plot_titlelocation
  * plot_titlevspan
  * pos
  * show
  * size
  * tex_output_standalone
  * thickness_scaling
  * warn_on_unsupported
  * window_title
