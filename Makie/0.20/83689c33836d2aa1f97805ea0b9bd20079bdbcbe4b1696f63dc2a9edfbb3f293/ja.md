```
ecdfplot(values; npoints=10_000[, weights])
```

`values`の経験的累積分布関数（ECDF）をプロットします。

`npoints`はプロットの解像度を制御します。値に対して`weights`が提供されている場合、加重ECDFがプロットされます。

## 属性

`MakieCore.Plot{Makie.ecdfplot}`の利用可能な属性とそのデフォルトは次のとおりです：

```
  alpha           1.0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  cycle           [:color]
  depth_shift     0.0f0
  highclip        MakieCore.Automatic()
  inspectable     true
  linestyle       "nothing"
  linewidth       1.5
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  space           :data
  ssao            false
  step            :pre
  transparency    false
  visible         true
```
