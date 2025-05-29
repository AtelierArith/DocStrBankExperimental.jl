```
image(x, y, image)
image(image)
```

Plots an image on range `x, y` (defaults to dimensions).

## Attributes

Available attributes and their defaults for `AbstractPlotting.Image` are: 

```
  ambient         Float32[0.55, 0.55, 0.55]
  colormap        [:black, :white]
  colorrange      AbstractPlotting.Automatic()
  diffuse         Float32[0.4, 0.4, 0.4]
  highclip        "nothing"
  inspectable     true
  interpolate     true
  lightposition   :eyeposition
  linewidth       1
  lowclip         "nothing"
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
