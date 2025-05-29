```
box_approximation(S::LazySet)
```

Overapproximate a set by a tight hyperrectangle.

### Input

  * `S` – set

### Output

A tight hyperrectangle.

### Notes

An alias for this function is `interval_hull`.

### Algorithm

The center and radius of the hyperrectangle are obtained by averaging the low and high coordinates of `S` computed with the `extrema` function.
