```
RenderModel
```

レンダリング指示と背景色を追跡するためのモデル。

  * `instruction_set::AbstractVector{Tuple}`: レンダリング指示のセット（関数、ctxを除く入力の配列、座標系）
  * `background_color::RGB`: 背景色

## フィールド

  * `instruction_set  :: AbstractVector{Tuple} = Array{Tuple}(undef, 0)`
  * `background_color :: RGB = colortheme["background"]`
