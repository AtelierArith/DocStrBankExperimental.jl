```
HistogramOverlay
```

指定された位置 `pos` にバーを表示します。バーのサイズは `width` と `height` で、与えられた高さの割合まで塗りつぶされます。塗りつぶしの割合は `val` を使用して設定され、0から1の間の数値である必要があります。0の場合、バーは塗りつぶされず、1の場合は上まで塗りつぶされます。

# フィールド

  * `pos::VecE2{Float64} = VecE2(0.,0.)`
  * `coordinate_system::Symbol = :scene`
  * `label::String = "histogram"`
  * `val::Float64 = 0.5` は0と1の間である必要があります
  * `width::Float64 = 2.`
  * `height::Float64 = 5.`
  * `fill_color::Colorant = colorant"blue"`
  * `line_color::Colorant = colorant"white"`
  * `font_size::Int64 = 15 # [pix]`
  * `label_pos::VecSE2{Float64} = pos + VecSE2(0., -height/2)` ラベルの位置
