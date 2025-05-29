```
reconstruct(M::SpatialPCA, y::AbstractVecOrMat{<:Real})
```

SpatialPCAモデル`M`を使用して、観測値`y`を元の空間におおよそ再構成します。

ここで、`y`は長さ`p`のベクトルまたは各列が観測値の成分を与える行列のいずれかです。
