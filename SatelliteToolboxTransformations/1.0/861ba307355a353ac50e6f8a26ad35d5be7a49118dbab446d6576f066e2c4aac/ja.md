```
r_mod_to_gcrf_fk5([T, ]jd_tt::Number) -> T
```

平均日 (MOD) フレームをユリウス日 [地球時] `jd_tt` における地心天球基準フレーム (GCRF) に整列させる回転を計算します。このアルゴリズムは IAU-76/FK5 理論を使用しています。

回転のタイプはオプションの変数 `T` によって説明されます。もしそれが `DCM` であれば、DCM が返されます。そうでなければ、`Quaternion` であれば Quaternion が返されます。このパラメータが省略された場合、DCM にフォールバックします。

# 戻り値

  * `T`: MOD フレームを GCRF フレームに整列させる回転。

# 備考

平均日 (MOD) フレームは、IAU 1976 年の歳差モデルを考慮して、地心天球基準フレーム (GCRF) に回転されます。

EOP 補正を考慮せずに `TOD => MOD` の変換が行われた場合、この回転によって得られる GCRF は通常 J2000 基準フレームと呼ばれるものです。
