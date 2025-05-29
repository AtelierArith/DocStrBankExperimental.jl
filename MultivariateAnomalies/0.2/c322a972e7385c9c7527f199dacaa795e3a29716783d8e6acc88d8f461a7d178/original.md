```
dist_matrix!(D_out, data, ...)
```

compute the distance matrix of `data`, similar to `dist_matrix()`. `D_out` object has to be preallocated, i.e. with `init_dist_matrix`.

# Examples

```
julia> dc = randn(10,4, 4,3)
julia> D_out = init_dist_matrix(dc)
julia> dist_matrix!(D_out, dc, lat = 2, lon = 2)
julia> D_out[1]
```
