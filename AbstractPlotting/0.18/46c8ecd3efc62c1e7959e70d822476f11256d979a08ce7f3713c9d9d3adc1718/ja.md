```
lines(positions)
lines(x, y)
lines(x, y, z)
```

`(x, y, z)`, `(x, y)` または `positions` の各要素に対して接続された線プロットを作成します。

!!! tip
    セグメントを分けるには `NaN` を挿入できます。


## 属性

`AbstractPlotting.Lines` の利用可能な属性とそのデフォルトは次のとおりです：

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
