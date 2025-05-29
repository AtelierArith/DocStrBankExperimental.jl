```
moment(M::AbstractManifold, x::AbstractVector, k::Int[, w::AbstractWeights], m=mean(M, x[, w]))
```

マンifold `M` 上の点 `x` の `k` 番目の中心モーメントを計算します。オプションで重み `w` および/または事前に計算された [`mean`](@ref mean(::AbstractManifold, args...)) を提供できます。
