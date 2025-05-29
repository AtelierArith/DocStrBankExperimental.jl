```
is_similar(d1::DualEdge, d2::DualEdge) :: Bool
```

Return `true` if d1 and d2 have the same twist and are connected to the same triangles.

This is only the case if `d1` and `d2` are the same edge, or if they are incident to a point of degree 2.
