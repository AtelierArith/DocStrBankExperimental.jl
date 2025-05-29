```
contour(x, y, z)
contour(z::Matrix)
```

Creates a contour plot of the plane spanning `x::Vector`, `y::Vector`, `z::Matrix`. If only `z::Matrix` is supplied, the indices of the elements in `z` will be used as the `x` and `y` locations when plotting the contour.

The attribute levels can be either

```
an Int that produces n equally wide levels or bands

an AbstractVector{<:Real} that lists n consecutive edges from low to high, which result in n-1 levels or bands
```

To add contour labels, use `labels = true`, and pass additional label attributes such as `labelcolor`, `labelsize`, `labelfont` or `labelformatter`.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.contour}` are: 

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
