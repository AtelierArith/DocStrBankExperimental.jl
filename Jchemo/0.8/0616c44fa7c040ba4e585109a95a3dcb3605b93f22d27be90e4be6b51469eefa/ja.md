```
transf(object::Union{Pcr, Spcr}, X; nlv = nothing)
```

適合したモデルと行列 X から潜在変数 (LVs = スコア) を計算します。

  * `object` : 適合したモデル。
  * `X` : LVs が計算される行列 (m, p)。
  * `nlv` : 考慮すべき LV の数。
