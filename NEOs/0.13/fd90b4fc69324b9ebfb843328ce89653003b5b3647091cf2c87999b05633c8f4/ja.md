```
DifferentialCorrections(res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x0::Vector{T}, idxs::AbstractVector{Int}) where {T <: Real}
```

最小二乗法のための `DifferentialCorrections{T}` オブジェクトを返します。

参照してください [`leastsquares`](@ref)。

## 引数

  * `res::AbstractVector{OpticalResidual{T, TaylorN{T}}}`: 残差のベクトル。
  * `x_0::Vector{T}`: 初期推定値。
  * `idxs::AbstractVector{Int}`: フィットのためのパラメータのサブセット。

!!! reference
    https://doi.org/10.1017/CBO9781139175371 のセクション 5.2 および 5.3 を参照してください。

