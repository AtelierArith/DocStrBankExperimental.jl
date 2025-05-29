```
smithplot(z; kwargs...)
```

Plot lines on the Smith Chart.

# Valid Keywords:

  * `color`  sets the color of the marker. Read `? scatter`.
  * `colormap = :viridis` sets the colormap that is sampled for numeric colors.
  * `linestyle = :rect` sets the pattern of the line e.g. :solid, :dot, :dashdot.
  * `line_width = 2.8` sets the width of the line in pixel units.
  * `label = nothing`
  * `reflection = false`: Specifies whether it is a normalized impedance or a reflection coefficient.
  * `freq = Float64[]` Array of frequencies associated with each represented value. Mainly used by `DataInspector`.
