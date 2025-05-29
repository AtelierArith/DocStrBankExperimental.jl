```
CartesianProductArray{N, S<:LazySet{N}} <: LazySet{N}
```

Type that represents the Cartesian product of a finite number of sets.

### Fields

  * `array` – array of sets

### Notes

The Cartesian product preserves convexity: if the set arguments are convex, then their Cartesian product is convex as well.
