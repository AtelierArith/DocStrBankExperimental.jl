```
self_intersections(points::AbstractVector{<:Point})
```

Finds all self intersections of in a continuous line described by `points`. Returns a Vector of indices where each pair `v[2i], v[2i+1]` refers two intersecting line segments by their first point, and a Vector of intersection points.

Note that if two points are the same, they will generate a self intersection unless they are consecutive segments. (The first and last point are assumed to be shared between the first and last segment.)
