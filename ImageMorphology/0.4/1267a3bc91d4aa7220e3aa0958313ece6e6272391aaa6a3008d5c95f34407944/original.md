```
centroids = component_centroids(labeled_array)
```

Compute the centroid of each label in the input labeled array. `centroids` is shifted to 0-based indexing vector so that the centroid of background pixels is `centroids[0]`.

The centroid of a finite set `X`, also known as geometric center, is calculated using `sum(X)/length(X)`. For label `i`, all (Cartesian) indices of pixels with label `i` are used to build the set `X`

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

julia> component_centroids(label)
5-element OffsetArray(::Vector{Tuple{Float64, Float64}}, 0:4) with eltype Tuple{Float64, Float64} with indices 0:4:
 (3.3333333333333335, 2.6666666666666665)
 (1.0, 3.0)
 (3.142857142857143, 1.5714285714285714)
 (4.285714285714286, 3.857142857142857)
 (2.6666666666666665, 4.666666666666667)
```

For gray images, labels can be computed by [`label_components`](@ref).
