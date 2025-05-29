```
Teukolsky_radial(s::Int, l::Int, m::Int, a, omega; data_type=Solutions._DEFAULTDATATYPE, ODE_algorithm=Solutions._DEFAULTSOLVER, tolerance=Solutions._DEFAULTTOLERANCE, method="auto")
```

指定されたモード（`s` スピン重み、`l` 調和指数、`m` 方位指数、`a` ケルスピンパラメータ、`omega` 周波数）に対して、地平線での純粋な入射境界条件（`IN`）と無限大での純粋な出射境界条件（`UP`）を持つテュコルスキー関数を計算します。

*実数* 周波数の場合、数値的内境界（rsin）と外境界（rsout）はそれぞれデフォルト値 `_DEFAULT_rsin` と `_DEFAULT_rsout` に設定され、地平線と無限大での漸近展開の順序は自動的に決定されます。*複素* 周波数の場合、数値的内境界と外境界は自動的に決定され、地平線と無限大での漸近展開の順序はそれぞれ `_DEFAULT_horizon_expansion_order_for_cplx_freq` と `_DEFAULT_infinity_expansion_order_for_cplx_freq` に設定されます。
