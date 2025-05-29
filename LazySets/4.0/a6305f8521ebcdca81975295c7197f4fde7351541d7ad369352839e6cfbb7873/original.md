```
isbounded(cap::Intersection)
```

Check whether an intersection of two sets is bounded.

### Input

  * `cap` – intersection of two sets

### Output

`true` iff the intersection is bounded.

### Algorithm

We first check if any of the wrapped sets is bounded. Otherwise we check boundedness via [`LazySets._isbounded_unit_dimensions`](@ref).
