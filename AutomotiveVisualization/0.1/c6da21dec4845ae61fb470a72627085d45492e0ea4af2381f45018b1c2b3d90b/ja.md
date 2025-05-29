```
NeighborsOverlay
```

車両とその隣接車両の間に線を描画します。隣接車両は、レーンに応じて異なる色でリンクされます。

# フィールド

  * `target_id::Int`
  * `color_L::Colorant = colorant"blue"`
  * `color_M::Colorant = colorant"green`
  * `color_R::Colorant = colorant"red"`
  * `line_width::Float64 = 0.5`
  * `textparams::TextParams = TextParams()`
