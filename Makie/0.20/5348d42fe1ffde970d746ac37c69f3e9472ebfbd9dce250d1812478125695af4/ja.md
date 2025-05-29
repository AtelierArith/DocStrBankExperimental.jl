```
contour(x, y, z)
contour(z::Matrix)
```

`x::Vector`、`y::Vector`、`z::Matrix`を含む平面の等高線プロットを作成します。`z::Matrix`のみが提供される場合、`z`内の要素のインデックスが等高線をプロットする際の`x`および`y`の位置として使用されます。

属性レベルは次のいずれかです。

```
n等幅のレベルまたはバンドを生成するInt

低から高までのn連続エッジをリストするAbstractVector{<:Real}、これによりn-1のレベルまたはバンドが生成されます
```

等高線ラベルを追加するには、`labels = true`を使用し、`labelcolor`、`labelsize`、`labelfont`、または`labelformatter`などの追加のラベル属性を渡します。

## 属性

`MakieCore.Plot{Makie.contour}`の利用可能な属性とそのデフォルトは次のとおりです。

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
