```
Equals{T} <: DE9IMPredicate{T}
Equals() = Equals(nothing)
```

`Equals`: Two geometries are equal if and only if they have the same boundary and interior points.

An `Equals` predicate returns true if the two geometries have the same boundary and interior points.
