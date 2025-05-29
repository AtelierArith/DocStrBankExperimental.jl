Structure which holds the solution from application of Newton-Krylov algorithm to a nonlinear problem.

For example

```
sol = newton(prob, NewtonPar())
```

## Fields

  * `u::Any`: solution
  * `prob::Any`: nonlinear problem, typically a `BifurcationProblem`
  * `residuals::Any`: sequence of residuals
  * `converged::Bool`: has algorithm converged?
  * `itnewton::Int64`: number of newton steps
  * `itlineartot::Any`: total number of linear iterations

## methods

  * `converged(sol)` return whether the solution has converged.
