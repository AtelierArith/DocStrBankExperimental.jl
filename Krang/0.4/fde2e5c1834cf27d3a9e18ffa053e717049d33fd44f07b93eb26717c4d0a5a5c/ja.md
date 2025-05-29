```julia
emission_inclination(
    pix::Krang.AbstractPixel,
    τ
) -> NTuple{6, Any}

```

Mino時間τにおける点の放射傾斜で、その画像が画面座標（`α`、`β`）に表示されます。

# 引数

  * `pix` : ピクセル情報
  * `τ` : Mino時間
