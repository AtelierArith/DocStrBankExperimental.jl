```
LevenbergMarquardt(res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x0::Vector{T}, idxs::AbstractVector{Int}) where {T <: Real}
```

最小二乗法の最適化のための `LevenbergMarquardt{T}` オブジェクトを返します。

関連情報として [`leastsquares`](@ref) を参照してください。

## 引数

  * `res::AbstractVector{OpticalResidual{T, TaylorN{T}}}`: 残差のベクトル。
  * `x_0::Vector{T}`: 初期推定値。
  * `idxs::AbstractVector{Int}`: フィットのためのパラメータのサブセット。

!!! reference
    https://numerical.recipes のセクション 15.5.2 を参照してください。

