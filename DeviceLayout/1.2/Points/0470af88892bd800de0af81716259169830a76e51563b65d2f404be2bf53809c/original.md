```
lowerleft{T}(A::AbstractArray{Point{T}})
```

Return the lower-left [`Point`](@ref) of the smallest bounding rectangle (with sides parallel to the x- and y-axes) that contains all points in `A`.

Example:

```jldoctest
julia> lowerleft([Point(2, 0), Point(1, 1), Point(0, 2), Point(-1, 3)])
2-element Point{Int64} with indices SOneTo(2):
 -1
  0
```
