```
pad_circular(x, pad::Tuple; [dims])
pad_circular(x, pad::Int; [dims])
```

Pad the array `x` "circularly" across the border by wrapping around values from the opposite side of `x`. 

`pad` can a tuple of integers `(l1, r1, ..., ln, rn)` of some length `2n` that specifies the left and right padding size for each of the dimensions in `dims`. If `dims` is not given,  it defaults to the first `n` dimensions.

If `pad` is an integer, it is applied on both sides on every dimension in `dims`. In this case, `dims`  defaults to the first `ndims(x)-2` dimensions  (i.e. excludes the channel and batch dimension). 

The pad length on either side in any dimension must not exceed the size of `x` in that dimension, i.e. `pad_circular` is not able to create abitrary sized tilings of `x`.

See also [`pad_repeat`](@ref), [`pad_reflect`](@ref), [`pad_symmetric`](@ref), and [`pad_constant`](@ref).

```jldoctest
julia> r = reshape(1:9, 3, 3)
3×3 reshape(::UnitRange{Int64}, 3, 3) with eltype Int64:
 1  4  7
 2  5  8
 3  6  9

julia> pad_circular(r, (1,2,1,2))
6×6 Matrix{Int64}:
 9  3  6  9  3  6
 7  1  4  7  1  4
 8  2  5  8  2  5
 9  3  6  9  3  6
 7  1  4  7  1  4
 8  2  5  8  2  5
```
