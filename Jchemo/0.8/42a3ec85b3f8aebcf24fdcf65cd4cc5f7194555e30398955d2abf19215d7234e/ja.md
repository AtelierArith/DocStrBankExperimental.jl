```
transf(object::Union{Pca, Fda}, X; nlv = nothing)
```

適合したモデルとXデータから主成分（PCs = スコア T）を計算します。

  * `object` : 適合したモデル。
  * `X` : PCsが計算されるXデータ。
  * `nlv` : 計算するPCの数。
