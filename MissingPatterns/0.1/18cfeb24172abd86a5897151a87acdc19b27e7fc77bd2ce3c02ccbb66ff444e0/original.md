plotmissing(df; plot*size=(1000, 800), orientation=:vertical, dpi=100, color*missing=:grey10, color*present=:white, line*color=:white, line*width=1, tick*step=5)

Plots a heatmap showing missing value patterns in a DataFrame.

# Arguments

  * `df`: The input DataFrame.
  * `plot_size`: Tuple specifying the size of the plot.
  * `orientation`: Orientation of the heatmap (`:vertical` or `:horizontal`).
  * `dpi`: Resolution of the plot.
  * `color_missing`: Color for missing values.
  * `color_present`: Color for present values.
  * `line_color`: Color of the grid lines.
  * `line_width`: Width of the grid lines.
  * `tick_step`: Step size for ticks on the axes.

# Returns

  * A heatmap plot.
