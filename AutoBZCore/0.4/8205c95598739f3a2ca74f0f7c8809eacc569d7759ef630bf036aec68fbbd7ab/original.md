```
solve(::IntegralProblem, ::IntegralAlgorithm; kws...)::IntegralSolution
```

Compute the solution to the given [`IntegralProblem`](@ref) using the given [`IntegralAlgorithm`](@ref) for the given keyword arguments to the solver (i.e. `abstol`, `reltol`, or `maxiters`).

## Keywords

  * `abstol`: an absolute error tolerance to get the solution to a specified number of absolute digits, e.g. 1e-3 requests accuracy to 3 decimal places.  Note that this number must have the same units as the integral. (default: nothing)
  * `reltol`: a relative error tolerance equivalent to specifying a number of significant digits of accuracy, e.g. 1e-4 requests accuracy to roughly 4 significant digits. (default: nothing)
  * `maxiters`: a soft upper limit on the number of integrand evaluations (default: `typemax(Int)`)

Solvers typically converge only to the weakest error condition. For example, a relative tolerance can be used in combination with a smaller-than necessary absolute tolerance so that the solution is resolved up to the requested significant digits, unless the integral is smaller than the absolute tolerance.
