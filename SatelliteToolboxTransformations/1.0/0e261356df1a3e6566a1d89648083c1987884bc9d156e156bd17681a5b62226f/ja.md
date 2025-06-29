```
r_mod_to_ers_iau2006([T, ]jd_tt::Number, δΔϵ_2000::Number = 0, δΔΨ_2000::Number = 0) -> T
```

地球の参照系（ERS）と平均日付（MOD）参照系をジュリアン日 `jd_tt` [地球時] で整列させる回転を計算します。このアルゴリズムはIAU-2006理論を使用しています。

傾斜の摂動（`δΔϵ_2000`）および経度の摂動（`δΔψ_2000`）[rad] に対する補正を提供することができます。これらは通常、IERS EOPデータから取得されます（[`fetch_iers_eop`](@ref) および [`compute_δΔϵ_δΔψ`](@ref] を参照）。これらの補正は、液体の地球コアの影響をモデル化する自由コア摂動（FCN）に関連しています。

回転のタイプはオプションの変数 `T` によって説明されます。もし `DCM` であれば、DCMが返されます。そうでなければ、`Quaternion` であれば、クォータニオンが返されます。このパラメータが省略された場合、`DCM` にフォールバックします。

# 戻り値

  * `T`: MODフレームをERSフレームに整列させる回転。
