```
dbscan(points::AbstractMatrix, radius::Real;
       [metric=Euclidean()],
       [min_neighbors=1], [min_cluster_size=1],
       [nntree_kwargs...]) -> DbscanResult
```

Cluster `points` using the DBSCAN (Density-Based Spatial Clustering of Applications with Noise) algorithm.

## Arguments

  * `points`: when `metric` is specified, the *d×n* matrix, where each column is a *d*-dimensional coordinate of a point; when `metric=nothing`, the *n×n* matrix of pairwise distances between the points
  * `radius::Real`: neighborhood radius; points within this distance are considered neighbors

Optional keyword arguments to control the algorithm:

  * `metric` (defaults to `Euclidean()`): the points distance metric to use, `nothing` means `points` is the *n×n* precalculated distance matrix
  * `min_neighbors::Integer` (defaults to 1): the minimal number of neighbors required to assign a point to a cluster "core"
  * `min_cluster_size::Integer` (defaults to 1): the minimal number of points in a cluster; cluster candidates with fewer points are discarded
  * `nntree_kwargs...`: parameters (like `leafsize`) for the `KDTree` constructor

## Example

```julia
points = randn(3, 10000)
# DBSCAN clustering, clusters with less than 20 points will be discarded:
clustering = dbscan(points, 0.05, min_neighbors = 3, min_cluster_size = 20)
```

## References:

  * Martin Ester, Hans-Peter Kriegel, Jörg Sander, and Xiaowei Xu, *"A density-based algorithm for discovering clusters in large spatial databases with noise"*, KDD-1996, pp. 226–231.
  * Erich Schubert, Jörg Sander, Martin Ester, Hans Peter Kriegel, and Xiaowei Xu, *"DBSCAN Revisited, Revisited: Why and How You Should (Still) Use DBSCAN"*, ACM Transactions on Database Systems, Vol.42(3)3, pp. 1–21, https://doi.org/10.1145/3068335
