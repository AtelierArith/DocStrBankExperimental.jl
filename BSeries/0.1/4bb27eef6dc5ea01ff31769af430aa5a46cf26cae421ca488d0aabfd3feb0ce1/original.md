```
compose(b, a; normalize_stepsize=false)
```

Compose the B-series `a` with the B-series `b`. It is assumed that the B-series `b` has the coefficient unity of the empty tree.

In the notation of Chartier, Hairer and Vilmart (2010), we have `compose(b, a) = b ⋅ a`. Note that this means that method `b` is applied first, followed by method `a`.

If `normalize_stepsize = true`, the coefficients of the returned B-series are divided by `2^order(t)` for each rooted tree `t`. This normalizes the step size so that the resulting numerical integrator B-series uses the same step size as the input series (instead of a doubled step size).

# References

Section 3.1 of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
