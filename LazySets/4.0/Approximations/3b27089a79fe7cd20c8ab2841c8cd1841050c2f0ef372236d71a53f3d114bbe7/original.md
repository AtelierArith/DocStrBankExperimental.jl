```
ballinf_approximation(S::LazySet)
```

Overapproximate a set by a tight ball in the infinity norm.

### Input

  * `S` – set

### Output

A tight ball in the infinity norm.

### Algorithm

The center and radius of the ball are obtained by averaging the low and high coordinates of `S` computed with the `extrema` function.
