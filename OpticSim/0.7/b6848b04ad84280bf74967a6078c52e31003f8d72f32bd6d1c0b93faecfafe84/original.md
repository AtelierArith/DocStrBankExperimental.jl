```
makemesh(poly::ConvexPolygon{N, T}, ::Int = 0) where {N, T<:Real} -> TriangleMesh
```

Create a triangle mesh that can be rendered by iterating on the polygon's edges and for each edge use the centroid as the third vertex of the triangle.
