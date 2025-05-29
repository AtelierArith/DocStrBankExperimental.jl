```
arc(origin, radius, start_angle, stop_angle; kwargs...)
```

This function plots a circular arc, centered at `origin` with radius `radius`, from `start_angle` to `stop_angle`. `origin` must be a coordinate in 2 dimensions (i.e., a `Point2`); the rest of the arguments must be `<: Number`.

Examples:

`arc(Point2f0(0), 1, 0.0, π)` `arc(Point2f0(1, 2), 0.3. π, -π)`

## Attributes

Available attributes and their defaults for `AbstractPlotting.Arc` are: 

```
  ambient         Float32[0.55, 0.55, 0.55]
  color           :black
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  cycle           [:color]
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  lightposition   :eyeposition
  linestyle       "nothing"
  linewidth       1.5
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  resolution      361
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
