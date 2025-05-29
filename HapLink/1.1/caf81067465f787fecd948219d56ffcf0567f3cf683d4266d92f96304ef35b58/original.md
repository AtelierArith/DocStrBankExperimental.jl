```
sumsliced(A::AbstractArray, dim::Int, pos::Int=1)
```

Sum all elements that are that can be referenced by `pos` in the `dim` dimension of `A`.

# Example

```jldoctest
julia> A = reshape(1:8, 2, 2, 2)
2×2×2 reshape(::UnitRange{Int64}, 2, 2, 2) with eltype Int64:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> sumsliced(A, 2)
14

julia> sumsliced(A, 2, 2)
22
```

Heavily inspired by Holy, Tim "Multidimensional algorithms and iteration" [https://julialang.org/blog/2016/02/iteration/#filtering_along_a_specified_dimension_exploiting_multiple_indexes](https://julialang.org/blog/2016/02/iteration/#filtering_along_a_specified_dimension_exploiting_multiple_indexes)
