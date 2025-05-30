```
Intersects{T} <: DE9IMPredicate{T}

Intersects(b)
Intersects()
```

`Intersects`: Two geometries intersect if they have any point in common.

An `Intersects` predicate returns true if the two geometries have at least one point in common.

If `Intersects` wraps an object passed to a predicate function, it must be the second argument B.
