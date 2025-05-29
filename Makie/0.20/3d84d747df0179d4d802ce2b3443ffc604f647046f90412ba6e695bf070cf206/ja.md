```
stem(xs, ys, [zs]; kwargs...)
```

指定された位置にマーカーをプロットし、`offset` に沿ってステムラインを延長します。

`offset` は数値である場合、2D の場合は y を、3D の場合は z を設定します。2D プロットの場合は Point2、3D プロットの場合は Point3 であることもできます。また、xs、ys、zs と同じ長さのこれらのいずれかのイテラブルであることもできます。

stem の変換特性は `PointBased` です。

## 属性

`MakieCore.Plot{Makie.stem}` の利用可能な属性とそのデフォルトは次のとおりです：

```
  color            :black
  colormap         :viridis
  colorrange       MakieCore.Automatic()
  colorscale       identity
  cycle            [[:stemcolor, :color, :trunkcolor] => :color]
  inspectable      true
  marker           :circle
  markersize       9
  offset           0
  stemcolor        :black
  stemcolormap     :viridis
  stemcolorrange   MakieCore.Automatic()
  stemlinestyle    "nothing"
  stemwidth        1.5
  strokecolor      :black
  strokewidth      0
  trunkcolor       :black
  trunkcolormap    :viridis
  trunkcolorrange  MakieCore.Automatic()
  trunklinestyle   "nothing"
  trunkwidth       1.5
  visible          true
```
