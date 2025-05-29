```
strel([T], X::AbstractArray)
```

Convert structuring element (SE) `X` to appropriate presentation format with element type `T`. This is a useful tool to generate SE that most ImageMorphology functions understand.

ImageMorphology currently supports two commonly used representations:

  * `T=CartesianIndex`: offsets to its center point. The output type is `Vector{CartesianIndex{N}}`.
  * `T=Bool`: connectivity mask where `true` indicates connected to its center point. The output type is `BitArray{N}`.

```jldoctest; setup=:(using ImageMorphology)
julia> se_mask = centered(Bool[1 1 0; 1 1 0; 0 0 0]) # connectivity mask
3×3 OffsetArray(::Matrix{Bool}, -1:1, -1:1) with eltype Bool with indices -1:1×-1:1:
 1  1  0
 1  1  0
 0  0  0

julia> se_offsets = strel(CartesianIndex, se_mask) # displacement offsets to its center point
3-element Vector{CartesianIndex{2}}:
 CartesianIndex(-1, -1)
 CartesianIndex(0, -1)
 CartesianIndex(-1, 0)

julia> se = strel(Bool, se_offsets)
3×3 OffsetArray(::BitMatrix, -1:1, -1:1) with eltype Bool with indices -1:1×-1:1:
 1  1  0
 1  1  0
 0  0  0
```

See also [`strel_diamond`](@ref) and [`strel_box`](@ref) for SE constructors for two special cases.
