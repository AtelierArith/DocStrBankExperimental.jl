```
smithscatter(z; kwargs...)
```

Scatter points on the Smith Chart.

# Valid Keywords:

  * `color`  sets the color of the marker. Read `? scatter`.
  * `colormap = :viridis` sets the colormap that is sampled for numeric colors.
  * `marker = :rect` sets the scatter marker.
  * `markersize = 9` sets the size of the marker.
  * `label = nothing`
  * `reflection = false`: Specifies whether it is a normalized impedance or a reflection coefficient.
  * `freq = Float64[]` Array of frequencies associated with each represented value. Mainly used Mainly used by `DataInspector`.
