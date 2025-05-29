```
r_teme_to_tod([T, ]jd_tt::Number[, δΔϵ_1980::Number = 0, δΔψ_1980::Number = 0]) -> T
```

真の赤道平均春分点 (TEME) フレームをジュリアンデイ `jd_tt` [地球時] の真の日時 (TOD) フレームに整列させる回転を計算します。このアルゴリズムは、IAU-76/FK5 理論と **[1]**(p. 233) における TEME 定義を使用しています。傾斜の摂動に対する補正 (`δΔϵ_1980`) [rad] および経度の補正 (`δΔψ_1980`) [rad] を提供することができ、これらは通常 IERS EOP データから取得されます (見よ [`fetch_iers_eop`](@ref))。

回転のタイプはオプションの変数 `T` によって説明されます。もし `DCM` であれば、DCM が返されます。そうでなければ、`Quaternion` であれば Quaternion が返されます。このパラメータが省略された場合、デフォルトで `DCM` に戻ります。

# 戻り値

  * `T`: TEME フレームを TOD フレームに整列させる回転。

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.

```
