```
transf(object::Mbpca, Xbl; nlv = nothing)
transfbl(object::Mbpca, Xbl; nlv = nothing)
```

適合したモデルから潜在変数（LVs = スコア）を計算します。

  * `object` : 適合したモデル。
  * `Xbl` : LVsが計算されるXデータのブロックのリスト（行列のベクトル）。
  * `nlv` : 計算するLVの数。
