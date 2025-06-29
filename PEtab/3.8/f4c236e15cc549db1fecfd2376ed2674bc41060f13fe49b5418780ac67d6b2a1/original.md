```
calibrate(prob::PEtabODEProblem, x0, alg; kwargs...)::PEtabOptimisationResult
```

From starting point `x0` using optimization algorithm `alg`, estimate unknown model parameters for `prob`, and get results as a `PEtabOptimisationResult`.

`x0` can be a `Vector` or a `ComponentArray`, where the individual parameters must be in the order expected by `prob`. To get a vector in the correct order, see [`get_x`](@ref).

A list of available and recommended optimization algorithms (`alg`) can be found in the documentation. Briefly, supported algorithms are from:

  * [Optim.jl](https://julianlsolvers.github.io/Optim.jl/stable/): `LBFGS()`, `BFGS()`,   or `IPNewton()` methods.
  * [Ipopt.jl](https://coin-or.github.io/Ipopt/): `IpoptOptimizer()` interior-point Newton   method.
  * [Fides.py](https://github.com/fides-dev/fides): `Fides()` Newton trust region method.

Different ways to visualize the parameter estimation result can be found in the documentation.

See also [`PEtabOptimisationResult`](@ref), [`Fides`](@ref) and [`IpoptOptimizer`](@ref)

## Keyword Arguments

  * `save_trace::Bool = false`: Whether to save the optimization trace of the objective   function and parameter vector. Only applicable for some algorithms; see the   documentation for details.
  * `options = DEFAULT_OPTIONS`: Configurable options for `alg`. The type and available   options depend on which package `alg` belongs to. For example, if `alg = IPNewton()`   from Optim.jl, `options` should be provided as an `Optim.Options()` struct. A list of   configurable options can be found in the documentation.
