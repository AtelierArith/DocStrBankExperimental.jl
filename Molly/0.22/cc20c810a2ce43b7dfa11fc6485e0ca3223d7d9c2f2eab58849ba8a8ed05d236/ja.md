```
GPUNeighborFinder(; eligible, dist_cutoff, special, n_steps_reorder, initialized)
```

[Eastman and Pande 2010](https://doi.org/10.1002/jcc.21413)からの非結合力/ポテンシャルエネルギーアルゴリズムを使用して、隣接リストの計算を回避します。

これはNVIDIA GPUで推奨される隣接者ファインダーです。
