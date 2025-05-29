```
Bisection()
```

If possible, will use the bisection method over `Float64` values. The bisection method starts with a bracketing interval `[a,b]` and splits it into two intervals `[a,c]` and `[c,b]`, If `c` is not a zero, then one of these two will be a bracketing interval and the process continues. The computation of `c` is done by `_middle`, which reinterprets floating point values as unsigned integers and splits there. It was contributed  by  [Jason Merrill](https://gist.github.com/jwmerrill/9012954). This method avoids floating point issues and when the tolerances are set to zero (the default) guarantees a "best" solution (one where a zero is found or the bracketing interval is of the type `[a, nextfloat(a)]`).

When tolerances are given, this algorithm terminates when the interval length is less than or equal to the tolerance `max(δₐ, 2abs(u)δᵣ)` with `u` in `{a,b}` chosen by the smaller of `|f(a)|` and `|f(b)|`, or  or the function value is less than `max(tol, min(abs(a), abs(b)) * rtol)`. The latter is used only if the default tolerances (`atol` or `rtol`) are adjusted.

When solving $f(x,p) = 0$ for $x^*(p)$ using `Bisection` one can not take the derivative directly via automatatic differentiation, as the algorithm is not differentiable. See [Sensitivity](https://juliamath.github.io/Roots.jl/stable/roots/#Sensitivity) in the documentation for alternatives.
