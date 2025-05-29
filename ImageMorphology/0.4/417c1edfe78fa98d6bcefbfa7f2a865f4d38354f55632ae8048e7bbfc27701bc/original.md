```
counts = component_lengths(labeled_array)
```

Count the number of each labels in the input labeled array. `counts` is shifted to 0-based indexing vector so that the number of background pixels is `counts[0]`.

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

julia> component_lengths(label)
5-element OffsetArray(::Vector{Int64}, 0:4) with eltype Int64 with indices 0:4:
 3
 5
 7
 7
 3
```

For gray images, labels can be computed by [`label_components`](@ref).
