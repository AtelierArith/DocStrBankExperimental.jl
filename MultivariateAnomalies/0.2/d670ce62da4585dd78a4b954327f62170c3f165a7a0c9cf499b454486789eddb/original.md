```
knn_dists(D, k::Int, temp_excl::Int = 0)
```

returns the k-nearest neighbors of a distance matrix `D`. Excludes `temp_excl` (default: `temp_excl = 0`) distances from the main diagonal of `D` to be also nearest neighbors.

# Examples

```
julia> dc = randn(20, 4,3)
julia> D = dist_matrix(dc, space = 2)
julia> knn_dists_out = knn_dists(D, 3, 1)
julia> knn_dists_out[5] # distances
julia> knn_dists_out[4] # indices
```
