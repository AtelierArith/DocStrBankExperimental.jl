```
DecomposeWRTPlane(PL::Plane, x::AbstractVector)
```

Takes vector from ambient space which is also element of the given plane and returns its coordinates with respect to the plane basis. That is, `DecomposeWRTPlane` is the inverse of the plane embedding function [`PlanarCoordinates`](@ref).
