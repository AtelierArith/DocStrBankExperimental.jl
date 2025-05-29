```
propagate_lyap(dynamics::D, jd0::V, tspan::T, q0::Vector{U},
    params::NEOParameters{T}) where {T <: Real, U <: Number, V <: Number, D}
```

軌道のリャプノフスペクトルを計算します。

# 引数

  * `dynamics::D`: 動的モデル関数。
  * `jd0::V`: 初期ユリウス日 (TDB)。
  * `tspan::T`: 積分の時間範囲 [ユリウス日単位]。
  * `q0::Vector{U}`: 初期条件のベクトル。
  * `params::NEOParameters{T}`: [`NEOParameters`](@ref)を参照してください。
