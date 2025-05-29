```
diam_norm(A::IntervalMatrix, p=Inf)
```

Return the diameter norm of the interval matrix.

### Input

  * `A` – interval matrix
  * `p` – (optional, default: `Inf`) the `p`-norm used; valid options are:        `1`, `2`, `Inf`

### Output

The operator norm, in the `p`-norm, of the scalar matrix obtained by taking the element-wise `diam` function, where `diam(x) := sup(x) - inf(x)` for an interval `x`.

### Notes

This function gives a measure of the *width* of the interval matrix.
