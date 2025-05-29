`local_minimization(minimization_problem, local_method, x)`

Perform a local minimization using `local_method`, starting from `x`.

The objective and the bounds are provided in `minimization_problem`, see [`MinimizationProblem`](@ref). `x` should be an `AbstractVector` of conforming dimension.

`local_method` can be a type for which a method is defined (recommended). However, it can also be a closure, in which case it will be called as `local_method(minimization_problem, x)`.

In both cases, it should return `nothing`, or a value which has the following properties:

  * `location`, an `AbstractVector` for the minimizer.
  * `value`, for the value of the objective at `location`. `Inf` (or equivalent) should be used for infeasible regions.

The returned value may have other properties too, these are useful for convergence diagnostics, debugging information, etc, these depend on the `local_method`.

Returning `nothing` is equivalent to `value == Inf`, but in some cases can work better for type inference as the method won't have to construct a counterfactual type.
