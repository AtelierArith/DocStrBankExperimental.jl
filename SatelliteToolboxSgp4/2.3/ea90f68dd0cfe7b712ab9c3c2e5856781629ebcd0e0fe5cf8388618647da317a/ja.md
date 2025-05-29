```
sgp4_init(epoch::Tepoch, n₀::Number, e₀::Number, i₀::Number, Ω₀::Number, ω₀::Number, M₀::Number, bstar::Number; kwargs...) where {Tepoch<:Number, T<:Number}
sgp4_init(tle::TLE; kwargs...) where T
```

SGP4軌道伝播器のデータ構造を作成し、初期化します。

# 引数

  * `epoch::Number`: 軌道要素のエポック [ユリウス日]。
  * `n₀::Number`: エポックでのSGPタイプ「平均」平均運動 [rad/min]。
  * `e₀::Number`: エポックでの「平均」離心率。
  * `i₀::Number`: エポックでの「平均」傾斜 [rad]。
  * `Ω₀::Number`: エポックでの「平均」昇交点の経度 [rad]。
  * `ω₀::Number`: エポックでの「平均」近点引数 [rad]。
  * `M₀::Number`: エポックでの「平均」平均異常 [rad]。
  * `bstar::Number`: 抵抗パラメータ (B*)。
  * `tle::TLE`: SPG4を初期化するためのTLE (参照: `TLE`)。

# キーワード

  * `spg4_gc::Sgp4Constants`: SPG4軌道伝播器定数 (参照: [`Sgp4Constants`](@ref))。   (**デフォルト** = `sgp4c_wgs84`)

# 戻り値

  * [`Sgp4Propagator`](@ref): 初期化されたパラメータを持つ構造体。
