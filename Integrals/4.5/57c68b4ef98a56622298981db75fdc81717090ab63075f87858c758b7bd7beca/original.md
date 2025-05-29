```julia
solve(prob::IntegralProblem, alg::SciMLBase.AbstractIntegralAlgorithm; kwargs...)
```

## Keyword Arguments

The arguments to `solve` are common across all of the quadrature methods. These common arguments are:

  * `maxiters` (the maximum number of iterations)
  * `abstol` (absolute tolerance in changes of the objective value)
  * `reltol` (relative tolerance  in changes of the objective value)
