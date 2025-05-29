```
LineSearchesJL(; method = LineSearches.Static(), autodiff = nothing,
    initial_alpha = true)
```

Wrapper over algorithms from [LineSearches.jl](https://github.com/JuliaNLSolvers/LineSearches.jl/). Allows automatic construction of the objective functions for the line search algorithms utilizing automatic differentiation for fast VJPs or JVPs.

!!! warning
    Needs `LineSearches.jl` to be explicitly loaded before using this functionality.


### Arguments

  * `method`: the line search algorithm to use. Defaults to `method = LineSearches.Static()`, which means that the step size is fixed to the value of `alpha`.
  * `autodiff`: the automatic differentiation backend to use for the line search. Must be specified if analytic jacobian/jvp/vjp is not available.
  * `initial_alpha`: the initial step size to use. Defaults to `true` (which is equivalent to `1`).
