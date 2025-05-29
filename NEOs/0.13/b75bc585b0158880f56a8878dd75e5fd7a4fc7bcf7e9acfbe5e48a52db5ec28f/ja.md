```
gauss_method(obs::Vector{RadecMPC{T}}, params::NEOParameters{T}) where {T <: Real}
gauss_method(observatories::Vector{ObservatoryMPC{T}}, dates::Vector{DateTime},
    α::Vector{U}, δ::Vector{U}, params::NEOParameters{T}) where {T <: Real, U <: Number}
```

初期軌道決定（IOD）のコアガウス法。

## 引数

  * `obs::Vector{RadecMPC{T}}`: 三つの観測。
  * `observatories::Vector{ObservatoryMPC{T}}`: 観測地点。
  * `dates::Vector{DateTime}`: 観測時刻。
  * `α::Vector{U}`: 赤経 [rad]。
  * `δ::Vector{U}`: 赤緯 [rad]。
  * `params::NEOParameters{T}`: [`NEOParameters`](@ref)の`Gauss Method Parameters`を参照。

!!! reference
    https://doi.org/10.1016/C2016-0-02107-1の274ページのアルゴリズム5.5を参照してください。

