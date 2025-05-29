```
KmppAlg <: SeedingAlgorithm
```

Kmeans++ seeding (`:kmpp`).

Chooses the seeds sequentially. The probability of a point to be chosen is proportional to the minimum cost of assigning it to the existing seeds.

# References

> D. Arthur and S. Vassilvitskii (2007). *k-means++: the advantages of careful seeding.* 18th Annual ACM-SIAM symposium on Discrete algorithms, 2007.

