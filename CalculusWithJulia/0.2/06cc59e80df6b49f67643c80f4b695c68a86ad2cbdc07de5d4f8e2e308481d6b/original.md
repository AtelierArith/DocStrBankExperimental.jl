```
riemann(f, a, b, n; method="right"
```

Compute an approximations to the definite integral of `f` over `[a,b]` using an equal-sized partition of size `n+1`.

method: `"right"` (default), `"left"`, `"trapezoid"`, `"simpsons"`, `"ct"`, `"m̃"` (minimum over interval), `"M̃"` (maximum over interval)

Example:

```
f(x) = exp(x^2)
riemann(f, 0, 1, 1000)   # default right-Riemann sums
riemann(f, 0, 1, 1000; method="left")       # left sums
riemann(f, 0, 1, 1000; method="trapezoid")  # use trapezoid rule
riemann(f, 0, 1, 1000; method="simpsons")   # use Simpson's rule
```
