```julia
emission_coordinates_fast_light(
    pix::Krang.AbstractPixel,
    τ
) -> Tuple{Any, Any, Any, Any, Any, Bool}

```

画面座標（`α`, `β`）に現れる点を、傾斜θoに位置する観測者のためにレイトレースします。

# 引数

  * `pix` : ピクセル情報
  * `τ` : ミノ時間
