```
surface(x, y, z)
```

Plots a surface, where `(x, y)`  define a grid whose heights are the entries in `z`. `x` and `y` may be `Vectors` which define a regular grid, **or** `Matrices` which define an irregular grid.

## Attributes

Available attributes and their defaults for `AbstractPlotting.Surface` are: 

```
  ambient         Float32[0.55, 0.55, 0.55]
  color           "nothing"
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  diffuse         Float32[0.4, 0.4, 0.4]
  highclip        "nothing"
  inspectable     true
  invert_normals  false
  lightposition   :eyeposition
  linewidth       1
  lowclip         "nothing"
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shading         true
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
