```
is_flippable(g::TriangulatedPolygon, src::Integer, dst::Integer) :: Bool
```

Return whether or not the edge can be flipped.

Note that for a triangulation of a convex polygon, the inner edges are always flippable,      while the outer edges cannot be flipped.    
