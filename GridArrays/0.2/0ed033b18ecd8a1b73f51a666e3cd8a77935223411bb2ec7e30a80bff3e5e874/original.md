```
struct PeriodicEquispacedGrid{T} <: AbstractEquispacedGrid{T}
```

A periodic equispaced grid is an equispaced grid that omits the right endpoint. It has step size (b-a)/n.

# Example

```jldocs
julia> PeriodicEquispacedGrid(4,0,1)
4-element PeriodicEquispacedGrid{Float64}:
 0.0
 0.25
 0.5
 0.75
```
