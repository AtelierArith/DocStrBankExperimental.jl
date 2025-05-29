```
symmetric_interval_hull(S::LazySet{N}) where {N}
```

Overapproximate a set by a tight hyperrectangle centered in the origin.

### Input

  * `S` – set

### Output

A tight hyperrectangle that is centrally symmetric wrt. the origin.

### Notes

An alias for this function is `box_approximation_symmetric`.

### Algorithm

The center of the box is the origin, and the radius is obtained via the `extrema` function.
