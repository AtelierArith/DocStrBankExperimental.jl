MinkowskiSumArray{N, S<:LazySet{N}} <: LazySet{N}

Type that represents the Minkowski sum of a finite number of sets.

### Fields

  * `array` – array of sets

### Notes

This type assumes that the dimensions of all elements match.

The `ZeroSet` is the neutral element and the `EmptySet` is the absorbing element for `MinkowskiSumArray`.

The Minkowski sum preserves convexity: if the set arguments are convex, then their Minkowski sum is convex as well.
