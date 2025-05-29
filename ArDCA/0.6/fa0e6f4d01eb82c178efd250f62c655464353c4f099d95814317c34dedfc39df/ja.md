```
loglikelihood(x0::Matrix{T}, arnet::ArNet) where {T<:Integer})
```

モデル `arnet` の下で `Matrix` `x0` から計算された対数尤度のベクトルを返します。`size(x0) == N,M` であり、ここで `N` はシーケンスの長さ、`M` はシーケンスの数です。返されるベクトルは `M` 要素を持ちます。
