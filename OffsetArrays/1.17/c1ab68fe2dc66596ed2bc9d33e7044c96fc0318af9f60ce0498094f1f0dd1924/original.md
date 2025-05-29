```
centered(A, cp=center(A)) -> Ao
```

Shift the center coordinate/point `cp` of array `A` to `(0, 0, ..., 0)`. Internally, this is equivalent to `OffsetArray(A, .-cp)`.

!!! compat "OffsetArrays 1.9"
    This method requires at least OffsetArrays 1.9.


# Examples

```jldoctest; setup=:(using OffsetArrays)
julia> A = reshape(collect(1:9), 3, 3)
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> Ao = OffsetArrays.centered(A); # axes (-1:1, -1:1)

julia> Ao[0, 0]
5

julia> Ao = OffsetArray(A, OffsetArrays.Origin(0)); # axes (0:2, 0:2)

julia> Aoo = OffsetArrays.centered(Ao); # axes (-1:1, -1:1)

julia> Aoo[0, 0]
5
```

Users are allowed to pass `cp` to change how "center point" is interpreted, but the meaning of the output array should be reinterpreted as well. For instance, if `cp = map(last, axes(A))` then this function no longer shifts the center point but instead the bottom-right point to `(0, 0, ..., 0)`. A commonly usage of `cp` is to change the rounding behavior when the array is of even size at some dimension:

```jldoctest; setup=:(using OffsetArrays)
julia> A = reshape(collect(1:4), 2, 2) # Ideally the center should be (1.5, 1.5) but OffsetArrays only support integer offsets
2×2 Matrix{Int64}:
 1  3
 2  4

julia> OffsetArrays.centered(A, OffsetArrays.center(A, RoundUp)) # set (2, 2) as the center point
2×2 OffsetArray(::Matrix{Int64}, -1:0, -1:0) with eltype Int64 with indices -1:0×-1:0:
 1  3
 2  4

julia> OffsetArrays.centered(A, OffsetArrays.center(A, RoundDown)) # set (1, 1) as the center point
2×2 OffsetArray(::Matrix{Int64}, 0:1, 0:1) with eltype Int64 with indices 0:1×0:1:
 1  3
 2  4
```

See also [`center`](@ref OffsetArrays.center).
