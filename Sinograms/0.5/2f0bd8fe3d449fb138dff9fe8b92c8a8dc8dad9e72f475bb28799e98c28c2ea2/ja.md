```
fbp!(image, sino ; orbit::Real = 180, kwargs...)
```

平行ビームシノグラムのサイズ `[nr × nϕ]` からの FBP 再構成。結果を `image` 行列に書き込みます。

# 入力

  * `sino::AbstractMatrix`

# `SinoPar` コンストラクタのオプション

  * `dr` : シノグラムの放射状間隔; デフォルトは 1
  * `orbit` : 度単位の角度範囲; デフォルトは 180
  * `orbit_start` : 度単位の角度範囲; デフォルトは 0

# `ImageGeom` のオプション

  * `dx`, `dy`, `deltas`, `offset_x`, `offset_y`, `offsets`
  * `rmax` マスクの最大半径

# オプション

  * `kwargs` : `plan_fbp` に渡される

# 出力

  * `image::AbstractMatrix` が変更されます
