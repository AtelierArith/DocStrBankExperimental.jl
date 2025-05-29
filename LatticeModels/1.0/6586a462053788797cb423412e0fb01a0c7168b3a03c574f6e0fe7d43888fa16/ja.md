```
dos(eig[, E; broaden])
dos(gf[, E; broaden])
```

与えられた固有系に対してエネルギー `E` でのDOS（状態密度）を計算します。`E` が指定されていない場合、与えられたエネルギーでのDOSを計算する関数が返されます。

## 引数

  * `eig` は `Eigensystem` または `HamiltonianEigensystem` です。
  * `gf` は `GreenFunction` です。
  * `E` はDOSが計算されるエネルギーです。

## キーワード引数

  * `broaden` はエネルギーレベルの広がり因子で、デフォルトは `0.1` です。
