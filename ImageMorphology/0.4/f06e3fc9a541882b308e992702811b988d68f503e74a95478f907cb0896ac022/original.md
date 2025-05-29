```
boxes = component_boxes(labeled_array)
```

Calculates the minimal bounding boxes for each label including the background label. The labels can be computed by [`label_components`](@ref).

Each bounding box is represented as a `CartesianIndices`. `boxes` is shifted to 0-based indexing vector so that background region is `boxes[0]`.

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

julia> boxes = component_boxes(label) # get bounding boxes of all regions
5-element OffsetArray(::Vector{CartesianIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}}, 0:4) with eltype CartesianIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}} with indices 0:4:
 CartesianIndices((2:5, 2:4))
 CartesianIndices((1:1, 1:5))
 CartesianIndices((2:5, 1:3))
 CartesianIndices((3:5, 3:5))
 CartesianIndices((2:3, 4:5))

julia> A[boxes[1]] # crop the image region with label 1
1×5 Matrix{Int64}:
 2  2  2  2  2

julia> A[boxes[4]] # crop the image region with label 4
2×2 Matrix{Int64}:
 0  1
 1  1
```
