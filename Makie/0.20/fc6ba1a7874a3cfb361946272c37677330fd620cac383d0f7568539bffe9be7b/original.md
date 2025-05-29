```
arc(origin, radius, start_angle, stop_angle; kwargs...)
```

This function plots a circular arc, centered at `origin` with radius `radius`, from `start_angle` to `stop_angle`. `origin` must be a coordinate in 2 dimensions (i.e., a `Point2`); the rest of the arguments must be `<: Number`.

Examples:

`arc(Point2f(0), 1, 0.0, π)` `arc(Point2f(1, 2), 0.3. π, -π)`

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.arc}` are: 

```
  alpha           1.0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  cycle           [:color]
  depth_shift     0.0f0
  highclip        MakieCore.Automatic()
  inspectable     true
  linestyle       "nothing"
  linewidth       1.5
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  resolution      361
  space           :data
  ssao            false
  transparency    false
  visible         true
```
