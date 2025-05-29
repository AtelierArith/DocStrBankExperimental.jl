```
sgp4(Δt::Number, tle::TLE; kwargs...)
sgp4(epoch::Tepoch, n₀::Number, e₀::Number, i₀::Number, Ω₀::Number, ω₀::Number, M₀::Number, bstar::Number; kwargs...) where {Tepoch<:Number, T<:Number}
```

SGP4構造体を初期化し、時間Δt [分]まで軌道を伝播させます。

# 引数

  * `epoch::Number`: 軌道要素のエポック [ユリウス日]。
  * `n₀::Number`: エポックにおけるSGPタイプ「平均」平均運動 [rad/min]。
  * `e₀::Number`: エポックにおける「平均」離心率。
  * `i₀::Number`: エポックにおける「平均」傾斜 [rad]。
  * `Ω₀::Number`: エポックにおける「平均」昇交点の経度 [rad]。
  * `ω₀::Number`: エポックにおける「平均」近点引数 [rad]。
  * `M₀::Number`: エポックにおける「平均」平均異常 [rad]。
  * `bstar::Number`: 抵抗パラメータ (B*)。
  * `tle::TLE`: SPG4を初期化するためのTLE（`TLE`を参照）。

# キーワード

  * `spg4_gc::Sgp4Constants`: SPG4軌道伝播器定数（[`Sgp4Constants`](@ref）を参照）。   (**デフォルト** = `sgp4c_wgs84`)

# 戻り値

  * `SVector{3, T}`: 位置ベクトル [km]。
  * `SVector{3, T}`: 速度ベクトル [km/s]。
  * [`Sgp4Propagator`](@ref): SGP4軌道伝播器構造体。
