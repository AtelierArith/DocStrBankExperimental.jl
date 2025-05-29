```
transf(object::Union{Mbplsr, Mbplswest}, Xbl; nlv = nothing)
```

適合したモデルから潜在変数 (LVs = スコア) を計算します。

  * `object` : 適合したモデル。
  * `Xbl` : LVs が計算される X データのブロックのリスト (行列のベクトル)。
  * `nlv` : 計算する LV の数。
