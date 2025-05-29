```
GeodesicDistance(DM::DataModel, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-10)
GeodesicDistance(Metric::Function, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-10)
```

Computes the length of a geodesic connecting the points `P` and `Q`.
