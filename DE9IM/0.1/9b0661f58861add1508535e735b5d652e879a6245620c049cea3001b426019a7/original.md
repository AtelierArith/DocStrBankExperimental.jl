```
Crosses{T} <: DE9IMPredicate{T}

Crosses(b)
Crosses()
```

`Crosses`: Geometry A crosses geometry B if and only if they have some but not all interior points in common.

A `Crosses` predicate returns true if the two geometries have some but not all interior points in common.
