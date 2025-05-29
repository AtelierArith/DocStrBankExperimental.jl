```
struct EquispacedGrid{T} <: AbstractEquispacedGrid{T}
```

An equispaced grid with n points on an interval [a,b], including the endpoints. It has step (b-a)/(n-1).

# Example

```jldocs
julia> EquispacedGrid(4,0,1)
4-element EquispacedGrid{Float64}:
 0.0
 0.3333333333333333
 0.6666666666666666
 1.0
```
