```
CachedMinkowskiSumArray{N, S<:LazySet{N}} <: LazySet{N}
```

Type that represents the Minkowski sum of a finite number of sets. Support vector queries are cached.

### Fields

  * `array` – array of sets
  * `cache` – cache for results of support-vector queries

### Notes

This type assumes that the dimensions of all sets in the array match.

The `ZeroSet` is the neutral element and the `EmptySet` is the absorbing element for `CachedMinkowskiSumArray`.

The cache (field `cache`) is implemented as a dictionary whose keys are direction vectors and whose values are pairs `(k, s)` where `k` is the number of elements in the array `array` when the support vector was evaluated last time, and `s` is the support vector that was obtained. Thus this type assumes that `array` is not modified except by adding new sets at the end.

The Minkowski sum preserves convexity: if all sets are convex, then their Minkowski sum is convex as well.
