```
NLsolveJL(;
    method = :trust_region, autodiff = :central, linesearch = Static(),
    linsolve = (x, A, b) -> copyto!(x, A\b), factor = one(Float64), autoscale = true,
    m = 10, beta = one(Float64)
)
```

### Keyword Arguments

  * `method`: the choice of method for solving the nonlinear system.
  * `autodiff`: the choice of method for generating the Jacobian. Defaults to `:central` or central differencing via FiniteDiff.jl. The other choices are `:forward` or `ADTypes` similar to other solvers in NonlinearSolve.
  * `linesearch`: the line search method to be used within the solver method. The choices are line search types from [LineSearches.jl](https://github.com/JuliaNLSolvers/LineSearches.jl).
  * `linsolve`: a function `linsolve(x, A, b)` that solves `Ax = b`.
  * `factor`: determines the size of the initial trust region. This size is set to the product of factor and the euclidean norm of `u0` if nonzero, or else to factor itself.
  * `autoscale`: if true, then the variables will be automatically rescaled. The scaling factors are the norms of the Jacobian columns.
  * `m`: the amount of history in the Anderson method. Naive "Picard"-style iteration can be achieved by setting m=0, but that isn't advisable for contractions whose Lipschitz constants are close to 1. If convergence fails, though, you may consider lowering it.
  * `beta`: It is also known as DIIS or Pulay mixing, this method is based on the acceleration of the fixed-point iteration xₙ₊₁ = xₙ + beta*f(xₙ), where by default beta = 1.

!!! warning
    Line Search Algorithms from [`LineSearch.jl`](https://github.com/SciML/LineSearch.jl) aren't supported by `NLsolveJL`. Instead, use the line search algorithms from [`LineSearches.jl`](https://github.com/JuliaNLSolvers/LineSearches.jl).


### Submethod Choice

Choices for methods in `NLsolveJL`:

  * `:anderson`: Anderson-accelerated fixed-point iteration
  * `:broyden`: Broyden's quasi-Newton method
  * `:newton`: Classical Newton method with an optional line search
  * `:trust_region`: Trust region Newton method (the default choice)

For more information on these arguments, consult the [NLsolve.jl documentation](https://github.com/JuliaNLSolvers/NLsolve.jl).

!!! note
    This algorithm is only available if `NLsolve.jl` is installed and loaded.

