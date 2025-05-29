```
overapproximate(cap::Intersection, ::Type{<:Interval})
```

Return the overapproximation of a lazy intersection with an interval.

### Input

  * `cap`      – one-dimensional intersection
  * `Interval` – target type

### Output

An interval.

### Algorithm

The algorithm recursively overapproximates the two intersected sets with intervals and then intersects these. (Note that this fails if the sets are unbounded.)

For convex sets this algorithm is precise.
