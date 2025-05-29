```
meshscatter(positions)
meshscatter(x, y)
meshscatter(x, y, z)
```

Plots a mesh for each element in `(x, y, z)`, `(x, y)`, or `positions` (similar to `scatter`). `markersize` is a scaling applied to the primitive passed as `marker`.

## Attributes

Available attributes and their defaults for `AbstractPlotting.MeshScatter` are: 

```
  ambient         Float32[0.55, 0.55, 0.55]
  color           :black
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  cycle           [:color]
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  lightposition   :eyeposition
  linewidth       1
  marker          GeometryBasics.Sphere{Float32}(Float32[0.0, 0.0, 0.0], 1.0f0)
  markersize      0.1
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  rotations       1.0 + 0.0im + 0.0jm + 0.0km
  shading         true
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
