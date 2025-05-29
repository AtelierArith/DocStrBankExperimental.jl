```
band(x, ylower, yupper; kwargs...)
band(lower, upper; kwargs...)
```

Plots a band from `ylower` to `yupper` along `x`. The form `band(lower, upper)` plots a [ruled surface](https://en.wikipedia.org/wiki/Ruled_surface) between the points in `lower` and `upper`.

## Attributes

Available attributes and their defaults for `AbstractPlotting.Band` are: 

```
  ambient         Float32[0.55, 0.55, 0.55]
  color           :black
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  cycle           [:color => :patchcolor]
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  interpolate     false
  lightposition   :eyeposition
  linewidth       1
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shading         true
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
