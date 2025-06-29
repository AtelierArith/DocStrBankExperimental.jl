```
r_tod_to_pef_fk5([T, ]jd_ut1::Number, jd_tt::Number[, δΔψ_1980::Number]) -> T
```

真の日時 (TOD) フレームをジュリアン日 `jd_ut1` [UT1] および `jd_tt` [地球時間] における擬似地球固定 (PEF) フレームに整列させる回転を計算します。このアルゴリズムは IAU-76/FK5 理論を使用しています。通常 IERS EOP データから取得される経度の摂動に対する補正 (`δΔψ_1980`) [rad] を提供することができます（[`fetch_iers_eop`](@ref) を参照）。

UT1 のジュリアン日はグリニッジ平均恒星時 (GMST) を計算するために使用されます（`jd_to_gmst` を参照）。一方、地球時間のジュリアン日は経度の摂動を計算するために使用されます。UT1 のジュリアン日と地球時間のジュリアン日は同等でなければならず、すなわち同じ瞬間に関連している必要があります。この関数は **これをチェックしません**。

回転のタイプはオプションの変数 `T` によって説明されます。もし `DCM` であれば、DCM が返されます。そうでなければ、`Quaternion` であれば、クォータニオンが返されます。このパラメータが省略された場合、`DCM` にフォールバックします。

# 戻り値

  * `T`: TOD フレームを PEF フレームに整列させる回転。

# 備考

真の日時 (TOD) フレームは、1980 年 IAU 摂動理論を考慮して擬似地球固定 (PEF) フレームに回転されます。地心天体基準系 (GCRS) と整合性を持たせるためには、IERS EOP 補正を追加する必要があります。
