```
LindgrenProcess(range=1.0, sill=1.0)
```

与えられた `range` と `sill` のLindgrenプロセス。

このプロセスはメッシュ上のラプラス-ベルタミ演算子の離散化に依存しており、特定のSPDEに関連しています。

## 例

```julia
# 範囲を設定
LindgrenProcess(20.0)

# 範囲とシルを設定
LindgrenProcess(20.0, 2.0)
```

## 参考文献

  * Lindgren et al. 2011. [An explicit link between Gaussian fields and Gaussian Markov random fields: the stochastic partial differential equation approach](https://rss.onlinelibrary.wiley.com/doi/10.1111/j.1467-9868.2011.00777.x)

### 注意事項

このプロセスは、単純なユークリッド距離とは異なり、測地線を近似するため、高度に曲がった領域（例：表面）で特に有用です。

文献では、ガウス・マルコフ確率場（GMRF）としても知られています。
