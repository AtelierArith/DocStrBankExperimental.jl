```
label = label_components(A; [dims=coords_spatial(A)], [r=1], [bkg])
label = label_components(A, se; [bkg])
```

Find and label the connected components of array `A` where the connectivity is defined by structuring element `se`. Each component is assigned a unique integer value as its label with `0` representing the background defined by `bkg`.

`se` is the structuring element that defines the neighborhood of the image. See [`strel`](@ref) for more details. If `se` is not specified, then it will use the [`strel_box`](@ref) with an extra keyword `dims` to control the dimensions to filter, and half-size `r` to control the diamond size.

# Examples

```jldoctest; setup=:(using ImageMorphology)
julia> A = [false true false true  false;
            true false false  true  true]
2×5 Matrix{Bool}:
 0  1  0  1  0
 1  0  0  1  1

julia> label_components(A) # default diamond shape C4 connectivity
2×5 Matrix{Int64}:
 0  2  0  3  0
 1  0  0  3  3

julia> label_components(A; dims=2) # only the rows are considered
2×5 Matrix{Int64}:
 0  2  0  3  0
 1  0  0  4  4

julia> label_components(A, strel_box((3, 3))) # box shape C8 connectivity
2×5 Matrix{Int64}:
 0  1  0  2  0
 1  0  0  2  2
```

The in-place version is [`label_components!`](@ref). See also [`component_boxes`](@ref), [`component_lengths`](@ref), [`component_indices`](@ref), [`component_centroids`](@ref) for basic properties of the labeled components.
