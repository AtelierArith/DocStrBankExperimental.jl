```
heatmap(x, y, values)
heatmap(values)
```

Plots a heatmap as an image on `x, y` (defaults to interpretation as dimensions).

## Attributes

Available attributes and their defaults for `AbstractPlotting.Heatmap` are: 

```
  ambient         Float32[0.55, 0.55, 0.55]
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  diffuse         Float32[0.4, 0.4, 0.4]
  highclip        "nothing"
  inspectable     true
  interpolate     false
  levels          1
  lightposition   :eyeposition
  linewidth       0.0
  lowclip         "nothing"
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
