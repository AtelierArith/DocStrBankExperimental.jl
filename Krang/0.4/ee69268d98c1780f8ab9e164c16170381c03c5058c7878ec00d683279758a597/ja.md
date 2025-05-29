```julia
emission_radius(
    pix::Krang.AbstractPixel,
    θs,
    isindir,
    n
) -> Tuple{Any, Any, Any, Any, Bool}

```

画面座標（`α`、`β`）に nth 順の画像が現れる傾斜 θs から発生する点の放射半径。 その画面座標に対して放射座標が存在しない場合は 0 を返します。

# 引数

  * `pix` : ピクセル情報
  * `θs` : 放射傾斜
  * `isindir` : 観測者への放射が直接か間接か
  * `n` : 画像インデックス
