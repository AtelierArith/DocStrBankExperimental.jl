```
FI_Expt(y1, y2, dx; ftype=:norm)
```

実験データに基づいて古典的フィッシャー情報（CFI）を計算します。

  * `y1`: 真の値 (x) で得られた実験データ。
  * `y2`: x+dx で得られた実験データ。
  * `dx`: パラメータの既知の小さなドリフト。
  * `ftype`: データが従う分布。オプションは: norm, gamma, rayleigh, および poisson です。
