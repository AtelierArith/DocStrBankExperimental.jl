```
compose(b1, b2, bs...; normalize_stepsize=false)
```

Compose the B-series `b1`, `b2`, `bs...`. It is assumed that all B-series have the coefficient unity of the empty tree.

In the notation of Chartier, Hairer and Vilmart (2010), we have `compose(b1, b2, b3) = b1 ⋅ b2 ⋅ b3`. Note that this product is associative and has to be read from left to right, i.e., method `b1` is applied first, followed by `b2`, `bs...`.

If `normalize_stepsize = true`, the coefficients of the returned B-series are divided by `n^order(t)` for each rooted tree `t`, where `n` is the total number of composed B-series. This normalizes the step size so that the resulting numerical integrator B-series uses the same step size as the input series (instead of an `n`-fold step size).

# References

Section 3.1 of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
