```
not(x)
```

Create a `NotIndex` with given `x`, which is similar to `Not` of [`InvertedIndices`](https://github.com/JuliaData/InvertedIndices.jl). In most cases, `not` is much faster than `Not`. See [performance comparing](@ref performance) for more details.

# Main differences between `not` and `Not`

For `CartesianIndex`, `A[not(CartesianIndex(i, j,..., n))]` is equivalent to `A[not(i), not(j), ..., not(n)]` and will return a array with same dimension, but `A[Not(CartesianIndex(i, j,..., n))]` will convert the `CartesianIndex` to a linear index and return a vector:

```jldoctest
julia> A = reshape(1:12, 3, 4)
3×4 reshape(::UnitRange{Int64}, 3, 4) with eltype Int64:
 0  3  6   9
 1  4  7  10
 2  5  8  11

julia> A[not(CartesianIndex(1, 2))] # equivalent to A[not(1), not(2)]
2×3 Matrix{Int64}:
 1  7  10
 2  8  11

julia> A[Not(CartesianIndex(1, 2))] # equivalent to A[Not(3)]
11-element Vector{Int64}:
  0
  1
  2
  4
  5
  ⋮
  8
  9
 10
 11
```

Besides, for index like `A[4, 5]` which is out of bounds, `A[not(4), not(5)]` is equivalent to `A[:, :]`, because inbounds indices are always not equal to the given value, while `A[Not[4], Not(5)]` causes an error.
