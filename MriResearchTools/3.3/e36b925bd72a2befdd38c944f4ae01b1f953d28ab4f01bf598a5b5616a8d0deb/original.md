```
to_dim(V::AbstractVector, dim::Int)

to_dim(a::Real, dim::Int)
```

Converts a vector or number to a higher dimension.

# Examples

```julia-repl
julia> to_dim(5, 3)
1×1×1 Array{Int64, 3}:
[:, :, 1] =
 5
julia> to_dim([1,2], 2)
 1×2 Matrix{Int64}:
  1  2
```
