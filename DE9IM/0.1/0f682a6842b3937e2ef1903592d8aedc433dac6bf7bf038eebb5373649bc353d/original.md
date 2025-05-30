```
Touches{T} <: DE9IMPredicate{T}

Touches(b)
Touches()
```

`Touches`: Two geometries touch if they have at least one point in common, but their interiors do not intersect.

A `Touches` predicate returns true if the two geometries have at least one point in common, but their interiors do not intersect.
