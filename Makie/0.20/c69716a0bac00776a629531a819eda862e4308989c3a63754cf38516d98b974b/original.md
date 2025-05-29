```
arrows(points, directions; kwargs...)
arrows(x, y, u, v)
arrows(x::AbstractVector, y::AbstractVector, u::AbstractMatrix, v::AbstractMatrix)
arrows(x, y, z, u, v, w)
arrows(x, y, [z], f::Function)
```

Plots arrows at the specified points with the specified components. `u` and `v` are interpreted as vector components (`u` being the x and `v` being the y), and the vectors are plotted with the tails at `x`, `y`.

If `x, y, u, v` are `<: AbstractVector`, then each 'row' is plotted as a single vector.

If `u, v` are `<: AbstractMatrix`, then `x` and `y` are interpreted as specifications for a grid, and `u, v` are plotted as arrows along the grid.

`arrows` can also work in three dimensions.

If a `Function` is provided in place of `u, v, [w]`, then it must accept a `Point` as input, and return an appropriately dimensioned `Point`, `Vec`, or other array-like output.

## Attributes

Available attributes and their defaults for `MakieCore.Arrows` are: 

```
  align           :origin
  alpha           1.0
  arrowcolor      MakieCore.Automatic()
  arrowhead       MakieCore.Automatic()
  arrowsize       MakieCore.Automatic()
  arrowtail       MakieCore.Automatic()
  backlight       0.0f0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  depth_shift     0.0f0
  diffuse         1.0
  highclip        MakieCore.Automatic()
  inspectable     true
  lengthscale     1.0f0
  linecolor       MakieCore.Automatic()
  linestyle       "nothing"
  linewidth       MakieCore.Automatic()
  lowclip         MakieCore.Automatic()
  markerspace     :pixel
  nan_color       :transparent
  normalize       false
  overdraw        false
  quality         32
  shading         MakieCore.Automatic()
  shininess       32.0f0
  space           :data
  specular        0.2
  ssao            false
  transparency    false
  visible         true
```
