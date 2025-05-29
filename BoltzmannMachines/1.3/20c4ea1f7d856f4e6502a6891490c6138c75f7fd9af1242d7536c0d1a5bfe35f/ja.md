```
logproblowerbound(dbm, x; ...)
logproblowerbound(dbm, x, logimpweights; ...)
logproblowerbound(dbm, x, logz; ...)
```

与えられたデータセット `x` に対する DBM の対数確率の変分下限の平均を推定します。これは [Salakhutdinov, 2015] の式 38 に記載されています。対数化された分配関数は、`logz` として直接指定するか、Annealed Importance Sampling アルゴリズム (AIS) を使用して分配関数を推定する際の `logimpweights` を提供することで指定できます。（`aislogimpweights` を参照してください。）`logimpweights` または `logz` のいずれも指定されていない場合、分配関数はデフォルトのパラメータを使用して AIS によって推定されます。

# オプションのキーワード引数:

  * 近似事後分布は引数 `mu` として与えることができるか、平均場法によって計算されます。
