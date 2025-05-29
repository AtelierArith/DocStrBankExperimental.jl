```
toeplitz(a::Vector{T}) where T
```

Transform vector `a` to a Toeplitz matrix.

# Examples

```julia-repl
julia> a = [1, 2, 3]; toeplitz(a)
2×2 Matrix{Int64}:
 2  1
 3  2
```
