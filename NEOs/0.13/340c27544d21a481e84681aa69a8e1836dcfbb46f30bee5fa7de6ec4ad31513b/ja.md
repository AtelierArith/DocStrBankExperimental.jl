```
propagate(dynamics::D, jd0::V, tspan::T, q0::Vector{U},
    params::NEOParameters{T}) where {T <: Real, U <: Number, V <: Number, D}
```

テイラー法を用いて軌道を統合します。初期ユリウス日 `jd0` はTDB時間スケールであると仮定されます。

## 引数

  * `dynamics::D`: 力学モデル関数。
  * `jd0::V`: 初期ユリウス日 (TDB)。
  * `tspan::T`: 統合の時間範囲 [年単位]。
  * `q0::Vector{U}`: 初期条件のベクトル。
  * `params::NEOParameters{T}`: [`NEOParameters`](@ref)を参照してください。
