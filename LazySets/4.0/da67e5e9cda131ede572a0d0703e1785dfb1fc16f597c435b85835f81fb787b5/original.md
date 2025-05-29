```
IntersectionArray{N, S<:LazySet{N}} <: LazySet{N}
```

Type that represents the intersection of a finite number of sets.

### Fields

  * `array` – array of sets

### Notes

This type assumes that the dimensions of all elements match.

The `EmptySet` is the absorbing element for `IntersectionArray`.

The intersection preserves convexity: if the set arguments are convex, then their intersection is convex as well.
