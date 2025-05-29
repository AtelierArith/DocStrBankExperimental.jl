```
Elkan()
```

Elkan algorithm implementation, based on "Charles Elkan. 2003. Using the triangle inequality to accelerate k-means. In Proceedings of the Twentieth International Conference on International Conference on Machine Learning (ICML’03). AAAI Press, 147–153."

This algorithm provides much faster convergence than Lloyd algorithm especially for high dimensional data. It can be used directly in `kmeans` function

```julia
X = rand(30, 100_000)   # 100_000 random points in 30 dimensions

kmeans(Elkan(), X, 3) # 3 clusters, Elkan algorithm
```
