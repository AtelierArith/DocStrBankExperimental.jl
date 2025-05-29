```
leastsquares(method::LS, res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x0::Vector{T} [, idxs::AbstractVector{Int}]; kwargs...) where {LS, T <: Real}
```

最小二乗法 `LS` を使用して、初期推定値 `x0` から始めて `res` の正規化平均二乗残差を最小化します。`idxs`（デフォルト: `eachindex(x0)`）が指定されている場合は、パラメータのサブセットに対して最小化を行います。

## キーワード引数

  * `maxiter::Int`: 最大反復回数（デフォルト: `25`）。
