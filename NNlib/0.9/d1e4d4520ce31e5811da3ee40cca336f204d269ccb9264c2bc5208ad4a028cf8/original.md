```
upsample_nearest(x, scale::NTuple{S,Int})
upsample_nearest(x; size::NTuple{S,Int})
```

Upsamples the array `x` by integer multiples along the first `S` dimensions. Subsequent dimensions of `x` are not altered.

Either the `scale` factors or the final output `size` can be specified.

See also [`upsample_bilinear`](@ref), for two dimensions of an `N=4` array.

# Example

```jldoctest
julia> upsample_nearest([1 2 3; 4 5 6], (2, 3))
4×9 Matrix{Int64}:
 1  1  1  2  2  2  3  3  3
 1  1  1  2  2  2  3  3  3
 4  4  4  5  5  5  6  6  6
 4  4  4  5  5  5  6  6  6

julia> ans == upsample_nearest([1 2 3; 4 5 6]; size=(4, 9))  # equivalent
true

julia> upsample_nearest([1 2 3; 4 5 6], (2,))
4×3 Matrix{Int64}:
 1  2  3
 1  2  3
 4  5  6
 4  5  6

julia> ans == upsample_nearest([1 2 3; 4 5 6], size=(4,))
true
```
