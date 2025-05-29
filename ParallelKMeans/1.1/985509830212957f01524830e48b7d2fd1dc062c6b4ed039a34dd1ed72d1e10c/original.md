```
Hamerly()
```

Hamerly algorithm implementation, based on "Hamerly, Greg. (2010). Making k-means Even Faster.  Proceedings of the 2010 SIAM International Conference on Data Mining. 130-140. 10.1137/1.9781611972801.12."

This algorithm provides much faster convergence than Lloyd algorithm with realtively small increase in memory footprint. It is especially suitable for low to medium dimensional input data.

It can be used directly in `kmeans` function

```julia
X = rand(30, 100_000)   # 100_000 random points in 30 dimensions

kmeans(Hamerly(), X, 3) # 3 clusters, Hamerly algorithm
```
