```
pf_adiabatic(freq, envs, ranges, zs, zr; n_modes = 41)
```

与えられた周波数に対する断熱圧力場を計算します。

必要な引数:

  * `freq`: 周波数 (Hz)
  * `envs`: 水中環境のリスト (Vector{Env})
  * `ranges`: 環境の範囲 (m)
  * `zs`: ソースの深さ (m)
  * `zr`: 受信機の深さ (m)
