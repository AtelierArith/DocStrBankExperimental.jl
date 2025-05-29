```
Muller(; middle = nothing)
```

Muller's method for determining a root of a univariate, scalar function.

The algorithm, described in Sec. 9.5.2 of [Press et al. (2007)](https://numerical.recipes/book.html), is a generalization of the secant method, using quadratic interpolation of three points to find the next estimate for the root. Due to the quadratic interpolation, the method is well suited for obtaining complex roots.

This method requires three initial guesses `(left, middle, right)` for the solution. The guesses `(left, right) = tspan` are provided by the `IntervalNonlinearProblem`, while the `middle` guess may be specified as an optional keyword argument. In notable contrast to the other `BracketingNonlinearSolve.jl` solvers, the `Muller` algorithm does not need `(left, right)` to bracket the root.

### Keyword Arguments

  * `middle`: the initial guess for the middle point. If not provided, the midpoint of the interval `(left, right)` is used.
