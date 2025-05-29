```julia
emission_radius(
    pix::Krang.AbstractPixel,
    τ
) -> Tuple{Any, Any, Any, Bool}

```

画面座標（`α`, `β`）に現れる点からの放射半径は、Mino時間τで発生します。画面座標に対して放射座標が存在しない場合は0を返します。

# 引数

-`pix` : ピクセル情報

  * `τ` : Mino時間
