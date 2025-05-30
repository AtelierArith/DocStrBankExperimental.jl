```
Disjoint{T} <: DE9IMPredicate{T}

Disjoint(b)
Disjoint()
```

`Disjoint`: Two geometries are disjoint if their intersection is empty.

A `Disjoint` predicate returns true if the two geometries have no points in common.

If `Disjoint` wraps an object passed to a predicate function, it must be the second argument B.
