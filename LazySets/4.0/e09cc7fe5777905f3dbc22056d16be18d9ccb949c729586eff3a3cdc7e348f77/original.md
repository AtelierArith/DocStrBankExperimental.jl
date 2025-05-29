```
ConvexHullArray{N, S<:LazySet{N}} <: ConvexSet{N}
```

Type that represents the symbolic convex hull of a finite number of sets.

### Fields

  * `array` – array of sets

### Notes

The `EmptySet` is the neutral element for `ConvexHullArray`.

A `ConvexHullArray` is always convex.

### Examples

Convex hull of 100 two-dimensional balls whose centers follow a sinusoidal:

```jldoctest
julia> b = [Ball2([2*pi*i/100, sin(2*pi*i/100)], 0.05) for i in 1:100];

julia> c = ConvexHullArray(b);
```
