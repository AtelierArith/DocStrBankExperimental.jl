```
MinkowskiSum{N, S1<:LazySet{N}, S2<:LazySet{N}} <: LazySet{N}
```

Type that represents the Minkowski sum of two sets, i.e., the set

$$
X ⊕ Y = \{x + y : x ∈ X, y ∈ Y\}.
$$

### Fields

  * `X` – set
  * `Y` – set

### Notes

The `ZeroSet` is the neutral element and the `EmptySet` is the absorbing element for `MinkowskiSum`.

The Minkowski sum preserves convexity: if the set arguments are convex, then their Minkowski sum is convex as well.
