```
squares_cdf(T_obs::Real, N::Integer)
```

P(T < T*obs | N)を計算します。これは、N回の独立した試行で観測されたT*obsの値におけるSquares統計量`T`の累積分布の値です。

`T_obs`は、観測データセットに対する検定統計量の値であり、すなわち、N回の独立した試行における期待値を上回る連続した観測値のいずれかの実行の中での最大の`χ^2`です。

`N`はデータポイントの総数です。

この計算は、以下の文献の式(16)および(17)を実装しています。

Frederik Beaujean and Allen Caldwell. *A Test Statistic for Weighted Runs.* Journal of Statistical Planning and Inference 141, no. 11 (November 2011): 3437–46. doi:10.1016/j.jspi.2011.04.022

https://arxiv.org/abs/1005.3233.
