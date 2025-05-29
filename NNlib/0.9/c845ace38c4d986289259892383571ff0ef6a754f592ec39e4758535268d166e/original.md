```
pad_symmetric(x, pad::Tuple; [dims])
pad_symmetric(x, pad::Int; [dims])
```

Pad the array `x` reflecting its values symmetrically across the border, i.e. the border values of `x` are present in the padding values, in contrast to [`pad_reflect`](@ref).

`pad` can a tuple of integers `(l1, r1, ..., ln, rn)` of some length `2n` that specifies the left and right padding size for each of the dimensions in `dims`. If `dims` is not given,  it defaults to the first `n` dimensions.

If `pad` is an integer, it is applied on both sides on every dimension in `dims`. In this case, `dims`  defaults to the first `ndims(x)-2` dimensions  (i.e. excludes the channel and batch dimension). 

See also [`pad_repeat`](@ref), [`pad_reflect`](@ref), [`pad_circular`](@ref), and [`pad_constant`](@ref).

```jldoctest
julia> r = reshape(1:9, 3, 3)
3×3 reshape(::UnitRange{Int64}, 3, 3) with eltype Int64:
 1  4  7
 2  5  8
 3  6  9

julia> pad_symmetric(r, (1,2,1,2))
6×6 Matrix{Int64}:
 1  1  4  7  7  4
 1  1  4  7  7  4
 2  2  5  8  8  5
 3  3  6  9  9  6
 3  3  6  9  9  6
 2  2  5  8  8  5
```
