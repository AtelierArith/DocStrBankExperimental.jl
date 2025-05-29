```
struct MidpointEquispacedGrid{T} <: AbstractEquispacedGrid{T}
```

A MidpointEquispaced grid is an equispaced grid with grid points in the centers of the equispaced subintervals. In other words, this is a DCT-II grid. It has step `(b-a)/n`.

# Example

```jldocs
julia> MidpointEquispacedGrid(4,0,1)
4-element MidpointEquispacedGrid{Float64}:
 0.125
 0.375
 0.6249999999999999
 0.875
```
