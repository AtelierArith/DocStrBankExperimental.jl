```
contour3d(x, y, z)
```

Creates a 3D contour plot of the plane spanning x::Vector, y::Vector, z::Matrix, with z-elevation for each level.

## Attributes

Available attributes and their defaults for `AbstractPlotting.Contour3d` are: 

```
  alpha           1.0
  ambient         Float32[0.55, 0.55, 0.55]
  color           "nothing"
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  diffuse         Float32[0.4, 0.4, 0.4]
  fillrange       false
  inspectable     true
  levels          5
  lightposition   :eyeposition
  linewidth       1.0
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
