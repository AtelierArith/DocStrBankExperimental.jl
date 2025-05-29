```julia
abstract type AbstractPolygon{D} <: AbstractShape{D} end
```

Abstract supertype for all polygons in `D`-dimensions. Non-polygons can be spheres, etc.
