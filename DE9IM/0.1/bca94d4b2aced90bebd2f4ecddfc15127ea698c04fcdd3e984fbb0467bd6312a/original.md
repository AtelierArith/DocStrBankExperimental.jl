```
Overlaps{T} <: DE9IMPredicate{T}
Overlaps() = Overlaps(nothing)
```

`Overlaps`: Geometry A overlaps geometry B if and only if they have some interior points in common.

An `Overlaps` predicate returns true if the two geometries have some interior points in common.
