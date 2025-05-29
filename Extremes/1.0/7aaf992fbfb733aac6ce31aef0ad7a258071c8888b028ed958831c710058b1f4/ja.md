```
quantile(fm::MaximumLikelihoodAbstractExtremeValueModel, p::Real)::Vector{<:Real}
```

適合したモデルからレベル `p` の分位数を計算します。非定常性の場合、有効な分位数が返されます。
