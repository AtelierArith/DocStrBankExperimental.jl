```
loglikelihood(x0::AbstractVector{T}, arnet::ArNet) where {T<:Integer}
```

整数値 `1:q` でエンコードされたシーケンス `x0` の対数尤度をモデル `arnet` の下で返します。
