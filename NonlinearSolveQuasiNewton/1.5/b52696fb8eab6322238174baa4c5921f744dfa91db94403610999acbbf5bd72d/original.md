```
Broyden(;
    max_resets::Int = 100, linesearch = nothing, reset_tolerance = nothing,
    init_jacobian::Val = Val(:identity), autodiff = nothing, alpha = nothing,
    update_rule = Val(:good_broyden)
)
```

An implementation of `Broyden`'s Method [broyden1965class](@cite) with resetting and line search.

### Keyword Arguments

  * `max_resets`: the maximum number of resets to perform. Defaults to `100`.
  * `reset_tolerance`: the tolerance for the reset check. Defaults to `sqrt(eps(real(eltype(u))))`.
  * `alpha`: If `init_jacobian` is set to `Val(:identity)`, then the initial Jacobian inverse is set to be `(αI)⁻¹`. Defaults to `nothing` which implies `α = max(norm(u), 1) / (2 * norm(fu))`.
  * `init_jacobian`: the method to use for initializing the jacobian. Defaults to `Val(:identity)`. Choices include:

      * `Val(:identity)`: Identity Matrix.
      * `Val(:true_jacobian)`: True Jacobian. This is a good choice for differentiable problems.
  * `update_rule`: Update Rule for the Jacobian. Choices are:

      * `Val(:good_broyden)`: Good Broyden's Update Rule
      * `Val(:bad_broyden)`: Bad Broyden's Update Rule
      * `Val(:diagonal)`: Only update the diagonal of the Jacobian. This algorithm may be useful for specific problems, but whether it will work may depend strongly on the problem
