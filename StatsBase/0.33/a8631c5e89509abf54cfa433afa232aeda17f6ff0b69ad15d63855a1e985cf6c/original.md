```
indicatormat(x, k::Integer; sparse=false)
```

Construct a boolean matrix `I` of size `(k, length(x))` such that `I[x[i], i] = true` and all other elements are set to `false`. If `sparse` is `true`, the output will be a sparse matrix, otherwise it will be dense (default).

# Examples

```jldoctest
julia> using StatsBase

julia> indicatormat([1 2 2], 2)
2×3 Matrix{Bool}:
 1  0  0
 0  1  1
```
