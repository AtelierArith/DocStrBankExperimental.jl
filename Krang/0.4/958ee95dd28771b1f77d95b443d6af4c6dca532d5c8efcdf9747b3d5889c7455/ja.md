```julia
emission_coordinates(
    pix::Krang.AbstractPixel,
    θs,
    isindir,
    n
) -> Tuple{Any, Any, Any, Any, Any, Bool}

```

発光半径と方位角は、傾斜角 θs から発生する点のもので、nth 順の画像が傾斜角 θo に位置する観測者の画面座標 (`α`, `β`) に現れます。

# 引数

  * `pix` : ピクセル情報
  * `θs` : 発光傾斜
  * `isindir` : 観測者への発光が直接か間接か
  * `n` : 画像インデックス
