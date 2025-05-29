```
gauss([T,] n)
gauss([T,] n, a, b)
```

Return a pair `(x, w)` of `n` quadrature points `x[i]` and weights `w[i]` to integrate functions on the interval $(a, b)$, which defaults to $(-1,1)$,  i.e. `sum(w .* f.(x))` approximates the integral $\int_a^b f(x) dx$.

Uses the Golub–Welch method described in Trefethen & Bau, Numerical Linear Algebra, to find the `n`-point Gaussian quadrature rule in O(`n`²) operations.

`T` is an optional parameter specifying the floating-point type, defaulting to `Float64`. Arbitrary precision (`BigFloat`) is also supported.  If `T` is not supplied,  but the interval `(a, b)` is passed, then the floating-point type is determined  from the types of `a` and `b`.
