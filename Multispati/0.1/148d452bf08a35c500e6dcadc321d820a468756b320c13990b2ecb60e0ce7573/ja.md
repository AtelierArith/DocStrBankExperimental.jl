```
predict(M::MULTISPATI, x::AbstractVecOrMat{<:Real})
```

モデル `M` を使って観測値 `x` を変換します。

ここで、`x` は長さ `d` のベクトルまたは各列が観測値である行列のいずれかです。
