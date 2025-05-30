```
stem(xs, ys, [zs]; kwargs...)
```

指定された位置にマーカーをプロットし、`offset` から茎の線に沿って延びます。

`offset` は数値であることができ、その場合は2Dの場合はyを、3Dの場合はzを設定します。2Dプロットの場合はPoint2、3Dプロットの場合はPoint3であることもできます。また、xs、ys、zsと同じ長さのこれらのいずれかのイテラブルであることもできます。

stemの変換特性は `PointBased` です。

## 属性

`AbstractPlotting.Stem` の利用可能な属性とそのデフォルトは次のとおりです：

```
  color            :black
  colormap         :viridis
  colorrange       AbstractPlotting.Automatic()
  cycle            [[:stemcolor, :color, :trunkcolor] => :color]
  inspectable      true
  marker           :circle
  markersize       9
  offset           0
  stemcolor        :black
  stemcolormap     :viridis
  stemcolorrange   AbstractPlotting.Automatic()
  stemlinestyle    "nothing"
  stemwidth        1.5
  strokecolor      :black
  strokewidth      0
  trunkcolor       :black
  trunkcolormap    :viridis
  trunkcolorrange  AbstractPlotting.Automatic()
  trunklinestyle   "nothing"
  trunkwidth       1.5
  visible          true
```
