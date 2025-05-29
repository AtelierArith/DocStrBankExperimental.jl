```
loglikelihood(x::AbstractMatrix{T}, lds::LinearDynamicalSystem{S,O}, y::AbstractMatrix{T}) where {T<:Real, S<:GaussianStateModel{T}, O<:GaussianObservationModel{T}}
```

観測データに基づく線形動的システム（LDS）の完全データ対数尤度を計算します。

# 引数

  * `x::AbstractMatrix{T}`: LDSの状態系列。
  * `lds::LinearDynamicalSystem{S,O}`: 線形動的システム。
  * `y::AbstractMatrix{T}`: 観測データ。
  * `w::Vector{Float64}`: データに重みを付けるための係数。

# 戻り値

  * `ll::T`: LDSの完全データ対数尤度。
