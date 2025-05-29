```
lines(positions)
lines(x, y)
lines(x, y, z)
```

Creates a connected line plot for each element in `(x, y, z)`, `(x, y)` or `positions`.

!!! tip
    You can separate segments by inserting `NaN`s.


## Attributes

Available attributes and their defaults for `AbstractPlotting.Lines` are: 

```
  ambient         Float32[0.55, 0.55, 0.55]
  color           :black
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  cycle           [:color]
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  lightposition   :eyeposition
  linestyle       "nothing"
  linewidth       1.5
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
