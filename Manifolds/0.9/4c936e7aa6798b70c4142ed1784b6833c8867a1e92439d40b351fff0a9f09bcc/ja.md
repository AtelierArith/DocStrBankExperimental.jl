```
skewness(M::AbstractManifold, x::AbstractVector, k::Int[, w::AbstractWeights], m=mean(M, x[, w]))
```

点 `x` の標準化された歪度を多様体 `M` 上で計算します。オプションで重み `w` および/または事前に計算された [`mean`](@ref mean(::AbstractManifold, args...)) `m` を提供できます。
