```
Contains{T} <: DE9IMPredicate{T}

Contains(b)
Contains()
```

`Contains`: Geometry A contains geometry B if and only if all points of B lie in the interior of A.

A `Contains` predicate returns true if all points of the second geometry lie in the interior of the first geometry.

If `Contains` wraps an object passed to a predicate function, it must be the second argument B.
