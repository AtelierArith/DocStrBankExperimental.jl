```
predict(M::HeteroPCAModel, x::AbstractVector; λ = 0.0)
```

**単一の観測ベクトル** `x` を推定された因子空間に投影し、観測された座標のみで重み付き最小二乗問題を解くことによって欠損エントリを処理します。

`λ` は、`rank` 座標が観測されていない場合にシステムを良好に定義するために、小さなリッジ（ティホノフ）正則化を追加します。
