```
flatten_batch(x::AbstractArray)
```

Merge the last two dimension.

# Example

```julia-repl
julia> x = reshape(1:12, 2, 2, 3)
2×2×3 reshape(::UnitRange{Int64}, 2, 2, 3) with eltype Int64:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

[:, :, 3] =
  9  11
 10  12

julia> flatten_batch(x)
2×6 reshape(::UnitRange{Int64}, 2, 6) with eltype Int64:
 1  3  5  7   9  11
 2  4  6  8  10  12
```
