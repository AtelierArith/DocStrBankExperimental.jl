```
Aspad = sym_paddedviews(fillvalue, A1, A2, ...; [dims])
```

Pad the arrays `A1`, `A2`, ..., to a common size or set of axes, chosen as the span of axes enclosing all of the input arrays.

The padding is applied to both directions in dimensions `dims`, which means original array located at the center the padded result. Use [`paddedviews`](@ref) if only one direction need to be padded.

The axes of original array `A` will be preserved in the padded result `Ap`, hence it's true that `Ap[CartesianIndices(A)] == A`.

```jldoctest
julia> using PaddedViews

julia> a1 = reshape([1, 2, 3], 3, 1)
3×1 Matrix{Int64}:
 1
 2
 3

julia> a2 = [4 5 6]
1×3 Matrix{Int64}:
 4  5  6

julia> a1p, a2p = sym_paddedviews(-1, a1, a2);

julia> a1p
3×3 PaddedView(-1, ::Matrix{Int64}, (1:3, 0:2)) with eltype Int64 with indices 1:3×0:2:
 -1  1  -1
 -1  2  -1
 -1  3  -1

julia> a2p
3×3 PaddedView(-1, ::Matrix{Int64}, (0:2, 1:3)) with eltype Int64 with indices 0:2×1:3:
 -1  -1  -1
  4   5   6
 -1  -1  -1

julia> a1p[CartesianIndices(a1)]
3×1 Matrix{Int64}:
 1
 2
 3
```

`dims` keyword allows padding only for specified dimensions.

```jldoctest; setup=:(using PaddedViews) julia> a1 = reshape(collect(1:9), 3, 3)  3×3 Matrix{Int64}:   1  4  7   2  5  8   3  6  9

julia> a2 = reshape([5, 6], 2, 1)  2×1 Matrix{Int64}:   5   6

julia> a1f, a2f = sym_paddedviews(-1, a1, a2; dims=1);

julia> a2f  3×1 PaddedView(-1, ::Matrix{Int64}, (1:3, 1:1)) with eltype Int64 with indices 1:3×1:1:    5    6   -1

julia> a1f, a2f = sym_paddedviews(-1, a1, a2; dims=(1,2));

julia> a2f  3×3 PaddedView(-1, ::Matrix{Int64}, (1:3, 0:2)) with eltype Int64 with indices 1:3×0:2:   -1   5  -1   -1   6  -1   -1  -1  -1  ```
