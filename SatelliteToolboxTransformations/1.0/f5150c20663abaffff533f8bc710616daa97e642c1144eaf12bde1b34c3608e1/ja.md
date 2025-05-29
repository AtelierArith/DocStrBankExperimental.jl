```
r_cirs_to_gcrf_iau2006([T, ]jd_tt::Number, δx::Number = 0, δy::Number = 0) -> T
```

天体中間基準系 (CIRS) をジュリアン日 `jd_tt` [TT] における地心天体基準系 (GCRF) に整列させる回転を計算します。IERS EOPデータ `δx` [rad] および `δy` [rad] を考慮します（[`fetch_iers_eop`](@ref) を参照）。このアルゴリズムはIAU-2006理論を使用しています。

IERS EOPデータ `δx` と `δy` は、GCRF に対する天体中間極 (CIP) の位置の自由コア揺動および時間依存効果を考慮しています。

回転のタイプはオプションの変数 `T` によって説明されます。`DCM` の場合、DCM が返されます。それ以外の場合、`Quaternion` であれば Quaternion が返されます。このパラメータが省略された場合、`DCM` にフォールバックします。

# 戻り値

  * `T`: CIRS フレームを GCRF フレームに整列させる回転。
