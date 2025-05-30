```
Covers{T} <: DE9IMPredicate{T}

Covers(b)
Covers()
```

Covers: Geometry A covers geometry B if and only if the intersection of A and B is equal to B.

A Covers predicate returns true if the intersection of the two geometries is equal to the second geometry.

If `Covers` wraps an object passed to a predicate function, it must be the second argument B.
