```
vrep(points::PointIt, lines::LineIt, rays::RayIt;
     d = Polyhedra.FullDim_rec(points, lines, rays))
```

Creates a V-representation for the polyhedron of full dimension `d` equal to the minkowski sum of the convex hull of `points` with the conic hull of `lines` and `rays`.
