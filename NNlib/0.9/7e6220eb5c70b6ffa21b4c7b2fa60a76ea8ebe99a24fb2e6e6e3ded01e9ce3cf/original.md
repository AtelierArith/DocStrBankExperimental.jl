```
pad_constant(x, pad::Tuple, val = 0; [dims = :])
pad_constant(x, pad::Int, val = 0; [dims = :])
```

Pad the array `x` with the constant value `val`.

`pad` can be a tuple of integers. If it is of some length `2 * length(dims)` that specifies the left and right padding size for each of the dimensions in `dims` as `(l1, r1, ..., ln, rn)`.  If supplied with a tuple of length `length(dims)` instead, it applies symmetric padding. If `dims` is not given, it defaults to all dimensions.

For integer `pad` input, it is applied on both sides on every dimension in `dims`.

See also [`pad_zeros`](@ref), [`pad_repeat`](@ref), [`pad_reflect`](@ref), [`pad_symmetric`](@ref), and [`pad_circular`](@ref).

```jldoctest
julia> r = reshape(1:4, 2, 2)
2×2 reshape(::UnitRange{Int64}, 2, 2) with eltype Int64:
 1  3
 2  4

julia> pad_constant(r, (1, 2, 3, 4), 8)
5×9 Matrix{Int64}:
 8  8  8  8  8  8  8  8  8
 8  8  8  1  3  8  8  8  8
 8  8  8  2  4  8  8  8  8
 8  8  8  8  8  8  8  8  8
 8  8  8  8  8  8  8  8  8

julia> pad_constant(r, 1, 8)
4×4 Matrix{Int64}:
 8  8  8  8
 8  1  3  8
 8  2  4  8
 8  8  8  8

julia> r = reshape(1:27, 3, 3, 3)
3×3×3 reshape(::UnitRange{Int64}, 3, 3, 3) with eltype Int64:
[:, :, 1] =
 1  4  7
 2  5  8
 3  6  9

[:, :, 2] =
 10  13  16
 11  14  17
 12  15  18

[:, :, 3] =
 19  22  25
 20  23  26
 21  24  27

julia> pad_constant(r, (2,1), dims = 1) # assymetric padding
6×3×3 Array{Int64, 3}:
[:, :, 1] =
 0  0  0
 0  0  0
 1  4  7
 2  5  8
 3  6  9
 0  0  0

[:, :, 2] =
  0   0   0
  0   0   0
 10  13  16
 11  14  17
 12  15  18
  0   0   0

[:, :, 3] =
  0   0   0
  0   0   0
 19  22  25
 20  23  26
 21  24  27
  0   0   0

julia> pad_constant(r, (2,1, 3), dims = (1,2)) # padding must always be either the same length as dims, or double it
ERROR: ArgumentError: Could not parse padding (2, 1, 3) and dims (1, 2)
Stacktrace:
[...]
```
