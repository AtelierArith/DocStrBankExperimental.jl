```
TextOverlay
```

指定した位置にテキストを表示します。座標とサイズの単位はデフォルトでピクセルです。オプション `coordinate_system` を使用すると、異なる単位を使用できます。

# フィールド

  * `text::Vector{String}`
  * `color::Colorant = colorant"white"`
  * `font_size::Int = 10`
  * `pos::VecE2 = VecE2(10, font_size)`
  * `line_spacing::Float64 = 1.5` `font_size` の倍数
  * `coordinate_system::Symbol=:camera_pixels`
