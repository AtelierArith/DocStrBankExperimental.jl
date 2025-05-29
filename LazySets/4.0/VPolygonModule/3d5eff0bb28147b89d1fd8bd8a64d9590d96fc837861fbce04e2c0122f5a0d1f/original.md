```
tohrep(P::VPolygon, ::Type{HPOLYGON}=HPolygon) where {HPOLYGON<:AbstractHPolygon}
```

Build a constraint representation of the given polygon.

### Input

  * `P`        – polygon in vertex representation
  * `HPOLYGON` – (optional, default: `HPolygon`) type of target polygon

### Output

A polygon in constraint representation, an `AbstractHPolygon`.

### Algorithm

The algorithm adds an edge for each consecutive pair of vertices. Since the vertices are already ordered in counter-clockwise fashion (CCW), the constraints will be sorted automatically (CCW).
