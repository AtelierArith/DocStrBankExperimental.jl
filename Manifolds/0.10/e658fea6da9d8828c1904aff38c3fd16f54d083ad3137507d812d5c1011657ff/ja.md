```
kurtosis(M::AbstractManifold, x::AbstractVector, k::Int[, w::AbstractWeights], m=mean(M, x[, w]))
```

マンフォールド `M` 上の点 `x` の超過尖度を計算します。オプションで重み `w` および/または事前に計算された [`mean`](@ref mean(::AbstractManifold, args...)) `m` を提供できます。
