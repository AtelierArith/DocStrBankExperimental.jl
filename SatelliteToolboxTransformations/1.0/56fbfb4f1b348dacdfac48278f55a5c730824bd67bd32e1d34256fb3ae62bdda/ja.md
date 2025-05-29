```
nutation_eo_iau2006(jd_tt::Number) -> NTuple{4, Float64}
```

ユリウス日 `jd_tt` [TT] における摂動パラメータと起源の方程式 (EO) を、春分点に基づく2006年IAU摂動理論を使用して計算します。通常、IERS EOPデータから取得される摂動の傾きに対する修正 (`δΔϵ_2000`) [rad] および経度に対する修正 (`δΔψ_2000`) [rad] を提供することができます（[`fetch_iers_eop`](@ref)を参照）。

# 戻り値

  * `Float64`: 黄道の平均傾き [rad]。
  * `Float64`: 黄道の傾きにおける摂動 [rad]。
  * `Float64`: 経度における摂動 [rad]。
  * `Float64`: 起源の方程式 (EO) [rad]。
