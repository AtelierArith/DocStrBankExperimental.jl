```
project(u::AbstractVector, v::AbstractVector) -> AbstractVector
```

Project vector `u` onto vector `v`.

# Examples

```jldoctest
julia> project([1, 1], [1, 0])
2-element Base.Vector{Float64}:
 1.0
 0.0

julia> project([5, 5], [1, 0])
2-element Base.Vector{Float64}:
 5.0
 0.0

julia> project([5, -5], [0, 1])
2-element Base.Vector{Float64}:
 -0.0
 -5.0
```
