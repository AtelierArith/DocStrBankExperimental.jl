```
stem(xs, ys, [zs]; kwargs...)
```

Plots markers at the given positions extending from `offset` along stem lines.

`offset` can be a number, in which case it sets y for 2D, and z for 3D stems. It can be a Point2 for 2D plots, as well as a Point3 for 3D plots. It can also be an iterable of any of these at the same length as xs, ys, zs.

The conversion trait of stem is `PointBased`.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.stem}` are: 

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
