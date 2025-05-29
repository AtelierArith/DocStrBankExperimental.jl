```
reconstruct(M::MULTISPATI, y::AbstractVecOrMat{<:Real})
```

モデル `M` を使用して、観測値 `y` を元の空間に近似的に再構成します。

ここで、`y` は長さ `p` のベクトルまたは各列が観測値の成分を与える行列のいずれかです。
