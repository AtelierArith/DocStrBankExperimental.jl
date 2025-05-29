```
Aspad = paddedviews(fillvalue, A1, A2, ...; [dims])
```

Pad the arrays `A1`, `A2`, ..., to a common size or set of axes, chosen as the span of axes enclosing all of the input arrays.

The padding is applied to one direction in dimensions `dims`. For example, values are filled to bottom-right part of the new array in two-dimensional case. Use [`sym_paddedviews`](@ref) if *both* directions need to be padded.

The axes of original array `A` will be preserved in the padded result `Ap`, hence it's true that `Ap[CartesianIndices(A)] == A`.

# Example:

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

julia> a1p, a2p = paddedviews(-1, a1, a2);

julia> a1p
3×3 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(3), Base.OneTo(3))) with eltype Int64:
 1  -1  -1
 2  -1  -1
 3  -1  -1

julia> a2p
3×3 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(3), Base.OneTo(3))) with eltype Int64:
  4   5   6
 -1  -1  -1
 -1  -1  -1

julia> a1p[CartesianIndices(a1)]
3×1 Matrix{Int64}:
 1
 2
 3
```

`dims` keyword allows padding only for specified dimensions.

```jldoctest; setup=:(using PaddedViews)
julia> a1 = reshape(collect(1:9), 3, 3)
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> a2 = [4 5;6 7]
2×2 Matrix{Int64}:
 4  5
 6  7

julia> a1f, a2f = paddedviews(-1, a1, a2; dims=1);

julia> a2f
3×2 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(3), Base.OneTo(2))) with eltype Int64:
  4   5
  6   7
 -1  -1

julia> a1f, a2f = paddedviews(-1, a1, a2; dims=(1,2));

julia> a2f
3×3 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(3), Base.OneTo(3))) with eltype Int64:
  4   5  -1
  6   7  -1
 -1  -1  -1
```
