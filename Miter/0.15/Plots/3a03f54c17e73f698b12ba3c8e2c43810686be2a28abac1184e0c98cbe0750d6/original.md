```julia
Plot(; ...)
Plot(contents; x_axis, y_axis, style, title)

```

Create a plot with the given `contents` (a vector, but a convenience form that accepts multiple arguments is available).

Keyword arguments (with defaults):

  * `x_axis = Axis.Linear()`, `y_axis = Axis.Linear()`: x and y axes
  * `style = PlotStyle()`: plot style (eg margins)
  * `title = nothing`: a title for the plot
