```
overapproximate(cap::IntersectionArray, ::Type{<:Interval})
```

Return the overapproximation of an intersection array with an interval.

### Input

  * `cap`      – one-dimensional intersection array
  * `Interval` – target type

### Output

An interval.

### Algorithm

The algorithm recursively overapproximates the intersected sets with intervals and then intersects these. (Note that this fails if the sets are unbounded.)

For convex sets this algorithm is precise.
