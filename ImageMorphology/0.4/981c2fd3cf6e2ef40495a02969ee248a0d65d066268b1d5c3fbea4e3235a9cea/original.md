```
indices = component_indices([T], labeled_array)
```

Get the indices of each label in the input labeled array. `indices` is shifted to 0-based indexing vector so that the indices of background pixels is `indices[0]`.

The optional type `T` can be either `Int`/`IndexLinear()` or `CartesianIndex`/`IndexCartesian()` that is used to specify the type of the indices. The default choice is `IndexStyle(labeled_array)`.

```jldoctest; setup=:(using ImageMorphology)
julia> A = [2 2 2 2 2; 1 1 1 0 1; 1 0 2 1 1; 1 1 2 2 2; 1 0 2 2 2]
5×5 Matrix{Int64}:
 2  2  2  2  2
 1  1  1  0  1
 1  0  2  1  1
 1  1  2  2  2
 1  0  2  2  2

julia> label = label_components(A) # four disjoint components
5×5 Matrix{Int64}:
 1  1  1  1  1
 2  2  2  0  4
 2  0  3  4  4
 2  2  3  3  3
 2  0  3  3  3

julia> indices = component_indices(label)
5-element OffsetArray(::Vector{Vector{Int64}}, 0:4) with eltype Vector{Int64} with indices 0:4:
 [8, 10, 17]
 [1, 6, 11, 16, 21]
 [2, 3, 4, 5, 7, 9, 12]
 [13, 14, 15, 19, 20, 24, 25]
 [18, 22, 23]

julia> indices = component_indices(CartesianIndex, label)
5-element OffsetArray(::Vector{Vector{CartesianIndex{2}}}, 0:4) with eltype Vector{CartesianIndex{2}} with indices 0:4:
 [CartesianIndex(3, 2), CartesianIndex(5, 2), CartesianIndex(2, 4)]
 [CartesianIndex(1, 1), CartesianIndex(1, 2), CartesianIndex(1, 3), CartesianIndex(1, 4), CartesianIndex(1, 5)]
 [CartesianIndex(2, 1), CartesianIndex(3, 1), CartesianIndex(4, 1), CartesianIndex(5, 1), CartesianIndex(2, 2), CartesianIndex(4, 2), CartesianIndex(2, 3)]
 [CartesianIndex(3, 3), CartesianIndex(4, 3), CartesianIndex(5, 3), CartesianIndex(4, 4), CartesianIndex(5, 4), CartesianIndex(4, 5), CartesianIndex(5, 5)]
 [CartesianIndex(3, 4), CartesianIndex(2, 5), CartesianIndex(3, 5)]
```

For gray images, labels can be computed by [`label_components`](@ref).
