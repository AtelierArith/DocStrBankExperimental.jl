```
PlaneCoordinates(PL::Plane, v::AbstractVector{<:Number})
```

Returns an n-dimensional vector from a tuple of two real numbers which correspond to the coordinates in the 2D `Plane`. That is, `PlanarCoordinates` provides an embedding of the plane parameters into the ambient space. The inverse function is given by [`DecomposeWRTPlane`](@ref).
