```
intersectionlength(v::AbstractVector{MinHashSketch})
```

Return a `length(v)` square `Matrix{Int}` where the `[i, j]` where `i > j`'th cell contain the number of hashes in both `v[i]` and `v[j]`.

# Examples

```julia-repl
julia> v = [sketch((1:1000) .+ (300*i), 100) for i in 1:4];

julia> intersectionlength(v)
4×4 Array{Int64,2}:
  0   0   0  0
 64   0   0  0
 27  58   0  0
  8  34  73  0
```
