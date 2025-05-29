```julia
init(prob::OptimizationProblem, alg::AbstractOptimizationAlgorithm, args...; kwargs...)
```

## Keyword Arguments

The arguments to `init` are the same as to `solve` and common across all of the optimizers. These common arguments are:

  * `maxiters` (the maximum number of iterations)
  * `maxtime` (the maximum of time the optimization runs for)
  * `abstol` (absolute tolerance in changes of the objective value)
  * `reltol` (relative tolerance  in changes of the objective value)
  * `callback` (a callback function)

Some optimizer algorithms have special keyword arguments documented in the solver portion of the documentation and their respective documentation. These arguments can be passed as `kwargs...` to `init`.

See also [`solve(prob::OptimizationProblem, alg, args...; kwargs...)`](@ref)
