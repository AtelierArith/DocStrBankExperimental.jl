```julia
solve(prob::NonlinearProblem, alg::Union{AbstractNonlinearAlgorithm,Nothing}; kwargs...)
```

## Arguments

The only positional argument is `alg` which is optional. By default, `alg = nothing`. If `alg = nothing`, then `solve` dispatches to the NonlinearSolve.jl automated algorithm selection (if `using NonlinearSolve` was done, otherwise it will error with a `MethodError`).

## Keyword Arguments

The NonlinearSolve.jl universe has a large set of common arguments available for the `solve` function. These arguments apply to `solve` on any problem type and are only limited by limitations of the specific implementations.

Many of the defaults depend on the algorithm or the package the algorithm derives from. Not all of the interface is provided by every algorithm. For more detailed information on the defaults and the available options for specific algorithms / packages, see the manual pages for the solvers of specific problems.

#### Error Control

  * `abstol`: Absolute tolerance.
  * `reltol`: Relative tolerance.

### Miscellaneous

  * `maxiters`: Maximum number of iterations before stopping. Defaults to 1e5.
  * `verbose`: Toggles whether warnings are thrown when the solver exits early. Defaults to true.

### Sensitivity Algorithms (`sensealg`)

`sensealg` is used for choosing the way the automatic differentiation is performed.     For more information, see the documentation for SciMLSensitivity:     https://docs.sciml.ai/SciMLSensitivity/stable/
