```
r_gcrf_to_teme([T, ]jd_tt::Number[, δΔϵ_1980::Number = 0, δΔψ_1980::Number = 0]) -> T
```

GCRFフレームを真の赤道平均春分点（TEME）フレームに整列させる回転を、ユリウス日`jd_tt` [地球時]で計算します。このアルゴリズムはIAU-76/FK5理論と**[1]**(p. 233)のTEME定義を使用します。通常、IERS EOPデータから取得される傾斜の摂動（`δΔϵ_1980`）[rad]および経度の摂動（`δΔψ_1980`）[rad]の補正を提供することができます（[`fetch_iers_eop`](@ref)を参照）。

回転のタイプはオプションの変数`T`によって説明されます。`DCM`の場合、DCMが返されます。それ以外の場合、`Quaternion`の場合はクォータニオンが返されます。このパラメータが省略された場合、`DCM`にフォールバックします。

!!! info
    傾斜の摂動（`δΔϵ_1980`）および経度の摂動（`δΔψ_1980`）に関連するEOPデータは省略できます。この場合、GCRFフレームは通常J2000基準フレームと呼ばれるものになります。


# 戻り値

  * `T`: GCRFフレームをTEMEフレームに整列させる回転。

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.

```
