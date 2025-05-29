```
KmppAlg <: SeedingAlgorithm
```

Kmeans++ シーディング (`:kmpp`)。

シードを順次選択します。ポイントが選ばれる確率は、既存のシードに割り当てる際の最小コストに比例します。

# 参考文献

> D. Arthur and S. Vassilvitskii (2007). *k-means++: the advantages of careful seeding.* 18th Annual ACM-SIAM symposium on Discrete algorithms, 2007.

