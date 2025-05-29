```
unsqueeze(x; dims)
```

Return `x` reshaped into an array one dimensionality higher than `x`, where `dims` indicates in which dimension `x` is extended. `dims` can be an integer between 1 and `ndims(x)+1`.

See also [`flatten`](@ref), `stack`.

# Examples

```jldoctest
julia> unsqueeze([1 2; 3 4], dims=2)
2×1×2 Array{Int64, 3}:
[:, :, 1] =
 1
 3

[:, :, 2] =
 2
 4


julia> xs = [[1, 2], [3, 4], [5, 6]]
3-element Vector{Vector{Int64}}:
 [1, 2]
 [3, 4]
 [5, 6]

julia> unsqueeze(xs, dims=1)
1×3 Matrix{Vector{Int64}}:
 [1, 2]  [3, 4]  [5, 6]
```
