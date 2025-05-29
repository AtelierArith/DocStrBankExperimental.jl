```
figure(; ...)
```

Create a new [`Figure`](@ref) and return it.

Acceptable keyword arguments are:

  * Anything taken by [`Figure`](@ref).
  * `x_range`/`y_range`: Sets the x/y-range. May be a vector of factors or a 2-tuple representing an interval. Default: `DataRange1d()`.
  * `x_axis`/`y_axis`: Sets the x/y-axis. May be `nothing` to suppress. Default: `LinearAxis()`.
  * `x_axis_location`/`y_axis_location`: Where to put the axis. One of `"left"`, `"right"`, `"above"` or `"below"`. Default: `"below"`/`"left"`.
  * `x_axis_label`/`y_axis_label`: Sets the label on the x/y-axis.
  * `x_grid`/`y_grid`: Sets the x/y-grid. May be `nothing` to suppress.
  * `tools`: Optional list of tools to create a toolbar from.
  * `tooltips`: If given, add a [`HoverTool`](@ref) with these tooltips.
