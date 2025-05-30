```
CoveredBy{T} <: DE9IMPredicate{T}

CoveredBy(b)
CoveredBy()
```

`CoveredBy`: Geometry A is covered by geometry B if and only if the intersection of A and B is equal to A.

A `CoveredBy` predicate returns true if the intersection of the two geometries is equal to the first geometry.

If `CoveredBy` wraps an object passed to a predicate function, it must be the second argument B.
