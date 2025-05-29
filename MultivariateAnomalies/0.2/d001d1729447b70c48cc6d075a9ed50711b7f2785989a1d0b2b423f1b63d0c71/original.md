```
knn_dists!(knn_dists_out, D, temp_excl::Int = 0)
```

returns the k-nearest neighbors of a distance matrix `D`. Similar to `knn_dists()`, but uses preallocated input object `knn_dists_out`, initialized with `init_knn_dists()`. Please note that the number of nearest neighbors `k` is not necessary, as it is already determined by the `knn_dists_out` object.

# Examples

```
julia> dc = randn(20, 4,3)
julia> D = dist_matrix(dc, space = 2)
julia> knn_dists_out = init_knn_dists(dc, 3)
julia> knn_dists!(knn_dists_out, D)
julia> knn_dists_out[5] # distances
julia> knn_dists_out[4] # indices
```
