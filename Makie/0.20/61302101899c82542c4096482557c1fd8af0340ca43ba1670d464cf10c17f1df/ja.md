```
wireframe(x, y, z)
wireframe(positions)
wireframe(mesh)
```

ワイヤーフレームを描画します。これは、表面またはメッシュとして解釈されます。

## 属性

`MakieCore.Wireframe` の利用可能な属性とそのデフォルト値は次のとおりです：

```
  alpha           1.0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  cycle           [:color]
  depth_shift     -1.0f-5
  highclip        MakieCore.Automatic()
  inspectable     true
  linestyle       "nothing"
  linewidth       1.5
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  space           :data
  ssao            false
  transparency    false
  visible         true
```
