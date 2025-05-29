```
sgp4_init!(sgp4d::Sgp4Propagator{Tepoch, T}, epoch::Number, n₀::Number, e₀::Number, i₀::Number, Ω₀::Number, ω₀::Number, M₀::Number, bstar::Number) where {Tepoch, T} -> Nothing
sgp4_init!(sgp4d::Sgp4Propagator{Tepoch, T}, tle::TLE) where {Tepoch, T} -> Nothing
```

引数で指定された初期軌道を使用してSGP4データ構造`sgp4d`を初期化します。

!!! warning
    `sgp4d`内の伝播定数`sgp4c::Sgp4PropagatorConstants`は変更されません。したがって、初期化する必要があります。


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
