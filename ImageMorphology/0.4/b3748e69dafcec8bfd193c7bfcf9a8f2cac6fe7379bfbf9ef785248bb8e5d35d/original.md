```
extreme_filter(f, A; r=1, [dims]) -> out
extreme_filter(f, A, Ω) -> out
```

Filter the array `A` using select function `f(x, y)` for each Ω-neighborhood. The name "extreme" comes from the fact that typical select function `f` choice is `min` and `max`.

For each pixel `p` in `A`, the select function `f` is applied to its Ω-neighborhood iteratively in a `f(...(f(f(A[p], A[p+Ω[1]]), A[p+Ω[2]]), ...)` manner. For instance, in the 1-dimensional case, `out[p] = f(f(A[p], A[p-1]), A[p+1])` for each `p` is the default behavior.

The Ω-neighborhood is defined by the `dims` or `Ω` argument. The `r` and `dims` keywords specifies the box shape neighborhood `Ω` using [`strel_box`](@ref). The `Ω` is also known as structuring element (SE), it can be either displacement offsets or bool array mask, please refer to [`strel`](@ref) for more details.

# Examples

```jldoctest extreme_filter; setup=:(using ImageMorphology)
julia> M = [4 6 5 3 4; 8 6 9 4 8; 7 8 4 9 6; 6 2 2 1 7; 1 6 5 2 6]
5×5 Matrix{Int64}:
 4  6  5  3  4
 8  6  9  4  8
 7  8  4  9  6
 6  2  2  1  7
 1  6  5  2  6

julia> extreme_filter(max, M) # max-filter using 4 direct neighbors along both dimensions
5×5 Matrix{Int64}:
 8  9  9  9  8
 8  9  9  9  9
 8  9  9  9  9
 8  8  9  9  9
 6  6  6  7  7

julia> extreme_filter(max, M; dims=1) # max-filter along the first dimension (column)
5×5 Matrix{Int64}:
 8  6  9  4  8
 8  8  9  9  8
 8  8  9  9  8
 7  8  5  9  7
 6  6  5  2  7
```

`Ω` can be either an `AbstractArray{Bool}` mask array with `true` element indicating connectivity, or a `AbstractArray{<:CartesianIndex}` array with each element indicating the displacement offset to its center element.

```jldoctest extreme_filter
julia> Ω_mask = centered(Bool[1 1 0; 1 1 0; 1 0 0]) # custom neighborhood in mask format
3×3 OffsetArray(::Matrix{Bool}, -1:1, -1:1) with eltype Bool with indices -1:1×-1:1:
 1  1  0
 1  1  0
 1  0  0

julia> out = extreme_filter(max, M, Ω_mask)
5×5 Matrix{Int64}:
 4  8  6  9  4
 8  8  9  9  9
 8  8  9  9  9
 7  8  8  9  9
 6  6  6  5  7

julia> Ω_offsets = strel(CartesianIndex, Ω_mask) # custom neighborhood as displacement offset
4-element Vector{CartesianIndex{2}}:
 CartesianIndex(-1, -1)
 CartesianIndex(0, -1)
 CartesianIndex(1, -1)
 CartesianIndex(-1, 0)

julia> out == extreme_filter(max, M, Ω_offsets) # both versions work equivalently
true
```

See also the in-place version [`extreme_filter!`](@ref). Another function in ImageFiltering package `ImageFiltering.mapwindow` provides similar functionality.
