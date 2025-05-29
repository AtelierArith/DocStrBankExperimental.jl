```
r_tod_to_teme([T, ]jd_tt::Number[, δΔϵ_1980::Number = 0, δΔψ_1980::Number = 0]) -> T
```

真の日時 (TOD) フレームをジュリアンデイ `jd_tt` [地球時] における真の赤道平均春分点 (TEME) フレームに整列させる回転を計算します。このアルゴリズムは IAU-76/FK5 理論と **[1]**(p.  233) における TEME 定義を使用しています。通常、IERS EOP データから取得される傾斜の摂動 (`δΔϵ_1980`) [rad] と経度の摂動 (`δΔψ_1980`) [rad] の補正を提供することができます（[`fetch_iers_eop`](@ref) を参照）。

回転のタイプはオプションの変数 `T` によって説明されます。`DCM` の場合、DCM が返されます。それ以外の場合、`Quaternion` の場合はクォータニオンが返されます。このパラメータが省略された場合、`DCM` にフォールバックします。

# 戻り値

  * `T`: TOD フレームを TEME フレームに整列させる回転。

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.

```
