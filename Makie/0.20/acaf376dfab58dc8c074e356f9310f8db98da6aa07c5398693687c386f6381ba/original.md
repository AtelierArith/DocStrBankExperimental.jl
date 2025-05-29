```
contour3d(x, y, z)
```

Creates a 3D contour plot of the plane spanning x::Vector, y::Vector, z::Matrix, with z-elevation for each level.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.contour3d}` are: 

```
  alpha           1.0
  color           "nothing"
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  depth_shift     0.0f0
  enable_depth    true
  highclip        MakieCore.Automatic()
  inspectable     true
  labelcolor      "nothing"
  labelfont       :regular
  labelformatter  Makie.contour_label_formatter
  labels          false
  labelsize       10
  levels          5
  linestyle       "nothing"
  linewidth       1.0
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  space           :data
  ssao            false
  transparency    false
  visible         true
```
