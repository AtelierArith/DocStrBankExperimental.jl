```
image(x, y, image)
image(image)
```

範囲 `x, y` に画像をプロットします（デフォルトは寸法です）。

## 属性

`AbstractPlotting.Image` の利用可能な属性とそのデフォルトは次のとおりです：

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
