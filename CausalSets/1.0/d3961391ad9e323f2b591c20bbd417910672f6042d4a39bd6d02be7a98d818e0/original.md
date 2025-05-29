```
BoxBoundary{N}(edges::Tuple{Coordinate{N}, Coordinate{N}}) <: AbstractBoundary{N}
```

The region specified by a rectangular box delimited by the pair of coordinates `edges`. Since this notion only makes sense for flat manifolds, it is currently implemented for [`MinkowskiManifold`](@ref) and [`TorusManifold`](@ref).

If this boundary is used with [`MinkowskiManifold`](@ref), the lower limit `edges[1][i]` needs to be smaller than `edges[2][i]` for every axis `1 ≤ i ≤ N`. In the case of [`TorusManifold`](@ref), the lower boundary can be higher than the upper boundary - in this case, the boundary will wrap around the torus.
