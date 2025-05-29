```
tryls(res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x0::Vector{T} [, idxs::AbstractVector{Int}]; kwargs...) where {T <: Real}
```

`res`の正規化された平均二乗残差の最小二乗最適化を、初期推定値`x0`から始めます。`idxs`（デフォルト: `eachindex(x0)`）が指定されている場合、パラメータのサブセットに対して最適化を行います。

関連情報として、[`LeastSquaresCache`](@ref)、[`AbstractLeastSquaresMethod`](@ref)、[`_lsmethods`](@ref)、および[`leastsquares!`](@ref)を参照してください。

## キーワード引数

  * `maxiter::Int`: 最大反復回数（デフォルト: `25`）。
  * `cache::LeastSquaresCache{T}`: 最小二乗キャッシュ（デフォルト: `LeastSquaresCache(x0, idxs, maxiter)`）。
  * `methods::Vector{AbstractLeastSquaresMethod}`: 試す最小二乗ルーチン（デフォルト: `_lsmethods(res, x0, idxs)`）。
