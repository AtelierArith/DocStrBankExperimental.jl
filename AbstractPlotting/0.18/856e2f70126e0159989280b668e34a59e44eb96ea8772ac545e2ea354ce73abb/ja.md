```
wireframe(x, y, z)
wireframe(positions)
wireframe(mesh)
```

ワイヤーフレームを描画します。これは、サーフェスまたはメッシュとして解釈されます。

## 属性

`AbstractPlotting.Wireframe` の利用可能な属性とそのデフォルト値は次のとおりです：

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
