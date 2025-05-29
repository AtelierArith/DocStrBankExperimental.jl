```
GeodesicBetween(DM::DataModel, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-10)
GeodesicBetween(Metric::Function, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-10)
```

Computes a geodesic between two given points on the parameter manifold and an expression for the metric.

Use keyword `BVPmeth` to pass a BVP integration algorithm from the `BoundaryValueDiffEq.jl` package. By setting the keyword `approx=true`, the ChristoffelSymbols are assumed to be constant and only computed once at the initial position. This simplifies the computation immensely but may also constitute an inaccurate approximation depending on the magnitude of the Ricci curvature.
