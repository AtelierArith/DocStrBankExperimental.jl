```
arrows(points, directions; kwargs...)
arrows(x, y, u, v)
arrows(x::AbstractVector, y::AbstractVector, u::AbstractMatrix, v::AbstractMatrix)
arrows(x, y, z, u, v, w)
```

Plots arrows at the specified points with the specified components. `u` and `v` are interpreted as vector components (`u` being the x and `v` being the y), and the vectors are plotted with the tails at `x`, `y`.

If `x, y, u, v` are `<: AbstractVector`, then each 'row' is plotted as a single vector.

If `u, v` are `<: AbstractMatrix`, then `x` and `y` are interpreted as specifications for a grid, and `u, v` are plotted as arrows along the grid.

`arrows` can also work in three dimensions.

## Attributes

Available attributes and their defaults for `AbstractPlotting.Arrows` are: 

```
  align           :origin
  ambient         Float32[0.55, 0.55, 0.55]
  arrowcolor      AbstractPlotting.Automatic()
  arrowhead       AbstractPlotting.Automatic()
  arrowsize       AbstractPlotting.Automatic()
  arrowtail       AbstractPlotting.Automatic()
  color           :black
  colormap        :viridis
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  lengthscale     1.0f0
  lightposition   :eyeposition
  linecolor       AbstractPlotting.Automatic()
  linestyle       "nothing"
  linewidth       AbstractPlotting.Automatic()
  markerspace     AbstractPlotting.Pixel
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  normalize       false
  overdraw        false
  quality         32
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
