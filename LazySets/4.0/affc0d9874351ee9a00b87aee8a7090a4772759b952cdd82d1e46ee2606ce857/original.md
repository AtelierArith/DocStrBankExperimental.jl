UnionSetArray{N, S<:LazySet{N}} <: LazySet{N}

Type that represents the set union of a finite number of sets.

### Fields

  * `array` – array of sets

### Notes

The union of convex sets is typically not convex.
