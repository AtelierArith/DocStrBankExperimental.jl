```
ldos(gf::GreenFunction, E[, site; broaden])
ldos(gf::GreenFunction, site[; broaden])
```

与えられたグリーン関数のエネルギー `E` に対する LDOS（局所状態密度）を計算します。`broaden` はエネルギーレベルのブロードニングファクターで、デフォルトは `0.1` です。

`site` が指定されていない場合、すべてのサイトの LDOS が計算され、`LatticeValue` として返されます。そうでない場合、指定されたサイトの LDOS が `Real` 値として返されます。

`E` が指定されていない場合、与えられたエネルギーに対してサイト `site` での LDOS を計算する関数が返されます。
