```
Within{T} <: DE9IMPredicate{T}

Within(b)
Within() = Within(nothing)
```

`Within`: Geometry A is within geometry B if and only if all points of A lie in the interior of B.

A `Within` predicate returns true if all points of the first geometry lie in the interior of the second geometry.

If `Within` wraps an object passed to a predicate function, it must be the second argument B.
