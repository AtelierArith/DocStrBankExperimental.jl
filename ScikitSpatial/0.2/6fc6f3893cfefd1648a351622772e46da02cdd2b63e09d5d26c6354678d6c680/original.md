```
project(point::AbstractVector, line::AbstractLine) -> StaticArrays.SVector
```

Project a point onto a line.

# Examples

```jldoctest
julia> project([1, 1], Line([0, 0], [1, 0]))
2-element StaticArrays.SVector{2, Float64} with indices SOneTo(2):
 1.0
 0.0

julia> project([5, -1], Line([0, 0], [1, 0]))
2-element StaticArrays.SVector{2, Float64} with indices SOneTo(2):
 5.0
 0.0

julia> project([1, 0], Line([0, 0], [1, 1]))
2-element StaticArrays.SVector{2, Float64} with indices SOneTo(2):
 0.5
 0.5

julia> point = project([1, 0, 0], Line([0, 0, 0], [1, 1, 1]));

julia> round.(point, digits=3)
3-element StaticArrays.SVector{3, Float64} with indices SOneTo(3):
 0.333
 0.333
 0.333
```
