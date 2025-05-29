```
ConvexPolygon{N, T<:Real} <: PlanarShape{T}
```

General Convex Polygon surface, not a valid CSG object. The rotation of the polygon around its normal is defined by `rotationvec`. `rotationvec×surfacenormal` is taken as the vector along the u axis.

```julia
ConvexPolygon(local_frame::Transform{T}, local_polygon_points::Vector{SVector{2, T}}, interface::NullOrFresnel{T} = nullinterface(T))
```

The local frame defines the plane (spans by the right and up vectors) with the plane normal given by the forward vector. the local*polygon*points are given with respect to the local frame and are 2D points. NOTE: This class uses static vectors to hold the points which will lead to more efficient performance, but should not be used with polygons with more than 20-30 points.
