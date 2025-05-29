```
heatmap(x, y, values)
heatmap(values)
```

`x, y` に画像としてヒートマップをプロットします（デフォルトでは次元として解釈されます）。

## 属性

`AbstractPlotting.Heatmap` の利用可能な属性とそのデフォルトは次のとおりです：

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
