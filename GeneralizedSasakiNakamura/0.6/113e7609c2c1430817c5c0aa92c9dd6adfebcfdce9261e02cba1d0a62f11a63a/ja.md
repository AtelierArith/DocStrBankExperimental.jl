```
GSN_radial(s::Int, l::Int, m::Int, a, omega; data_type=Solutions._DEFAULTDATATYPE, ODE_algorithm=Solutions._DEFAULTSOLVER, tolerance=Solutions._DEFAULTTOLERANCE, method="auto")
```

指定されたモード（`s` スピン重み、`l` ハーモニックインデックス、`m` 方位インデックス、`a` ケルスピンパラメータ、`omega` 周波数）に対して GSN 関数を計算します。境界条件は、地平線での純粋に入射する境界条件（`IN`）と無限大での純粋に出射する境界条件（`UP`）です。

*実数* 周波数の場合、数値的内境界 (rsin) と外境界 (rsout) はそれぞれデフォルト値 `_DEFAULT_rsin` と `_DEFAULT_rsout` に設定され、地平線と無限大での漸近展開の順序は自動的に決定されます。*複素* 周波数の場合、数値的内境界と外境界は自動的に決定され、地平線と無限大での漸近展開の順序はそれぞれ `_DEFAULT_horizon_expansion_order_for_cplx_freq` と `_DEFAULT_infinity_expansion_order_for_cplx_freq` に設定されます。
