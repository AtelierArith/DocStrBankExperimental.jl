```
squares_pvalue(T_obs::Real, N::Integer)
```

`T_obs`に対して`N`の条件付きでP(T >= `T_obs`)を計算します。これは、`N`のデータポイントで観測されたSquares統計量`T`が`T_obs`以上である確率値です。

Squares統計量`T`は、N回の独立した試行のシーケンスにおける期待値を上回る連続成功のいずれかの実行の最大`χ^2`を示します。

この関数は、Frederik BeaujeanとAllen Caldwellによる以下の論文の式(16)および(17)を実装しています。

Frederik Beaujean and Allen Caldwell. *A Test Statistic for Weighted Runs.* Journal of Statistical Planning and Inference 141, no. 11 (November 2011): 3437–46. doi:10.1016/j.jspi.2011.04.022

https://arxiv.org/abs/1005.3233.
