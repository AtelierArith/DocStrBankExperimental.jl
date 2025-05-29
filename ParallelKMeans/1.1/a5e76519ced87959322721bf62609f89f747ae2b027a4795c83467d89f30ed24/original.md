```
MiniBatch(b::Int)
`b` represents the size of the batch which should be sampled.

Sculley et al. 2007 Mini batch k-means algorithm implementation.
```

```julia
X = rand(30, 100_000)  # 100_000 random points in 30 dimensions

kmeans(MiniBatch(100), X, 3)  # 3 clusters, MiniBatch algorithm with 100 batch samples at each iteration
```
