```
predict(M::SpatialPCA, x::AbstractVecOrMat{<:Real})
```

SpatialPCAモデル`M`を使用して観測値`x`を変換します。

ここで、`x`は長さ`d`のベクトルまたは各列が観測値である行列のいずれかです。
