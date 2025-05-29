```
intersection(P1::AbstractHPolygon, P2::AbstractHPolygon; [prune]::Bool=true)
```

Compute the intersection of two polygons in constraint representation.

### Input

  * `P1`    – polygon in constraint representation
  * `P2`    – polygon in constraint representation
  * `prune` – (optional, default: `true`) flag for removing redundant constraints

### Output

If the polygons do not intersect, the result is the empty set. Otherwise the result is the polygon that describes the intersection.

### Algorithm

We just combine the constraints of both polygons. To obtain a linear-time algorithm, we interleave the constraints. If there are two constraints with the same normal vector, we choose the tighter one.

Redundancy of constraints is checked with [`remove_redundant_constraints!(::AbstractHPolygon)`](@ref).
