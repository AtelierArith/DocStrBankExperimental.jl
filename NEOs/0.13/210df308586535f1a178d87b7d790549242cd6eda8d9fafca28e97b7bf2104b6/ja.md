```
outlier_rejection!(res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x::Vector{T}, Γ::Matrix{T} [, cache::OutlierRejectionCache{T}];
    kwargs...) where {T <: Real}
```

Carpino et al. (2003) の外れ値除去アルゴリズム。

See also [`carpino_smoothing`](@ref).

## 引数

  * `res::AbstractVector{OpticalResidual{T, TaylorN{T}}}`: 残差のベクトル。
  * `x::Vector{T}`: 評価デルタ。
  * `Γ::Matrix{T}`: 共分散行列。
  * `cache::OutlierRejectionCache{T}`: see [`OutlierRejectionCache`](@ref).

## キーワード引数

  * `χ2_rec::T`: 回復閾値 (デフォルト: `7.0`)。
  * `χ2_rej::T`: 除去閾値 (デフォルト: `8.0`)。
  * `fudge::T`: 除去ファッジ項係数 (デフォルト: `400.0`)。
  * `α::T`: 最大カイのスケーリング係数 (デフォルト: `0.25`)。
  * `max_per::T`: 許可される最大ドロップ割合 (デフォルト: `10.0`)。

!!! reference
    See https://doi.org/10.1016/S0019-1035(03)00051-4.

