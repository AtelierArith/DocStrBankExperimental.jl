```
Klement(;
    max_resets = 100, linsolve = nothing, linesearch = nothing,
    alpha = nothing, init_jacobian::Val = Val(:identity),
    autodiff = nothing
)
```

An implementation of `Klement` [klement2014using](@citep) with line search, preconditioning and customizable linear solves. It is recommended to use [`Broyden`](@ref) for most problems over this.

### Keyword Arguments

  * `max_resets`: the maximum number of resets to perform. Defaults to `100`.
  * `alpha`: If `init_jacobian` is set to `Val(:identity)`, then the initial Jacobian inverse is set to be `αI`. Defaults to `1`. Can be set to `nothing` which implies `α = max(norm(u), 1) / (2 * norm(fu))`.
  * `init_jacobian`: the method to use for initializing the jacobian. Defaults to `Val(:identity)`. Choices include:

      * `Val(:identity)`: Identity Matrix.
      * `Val(:true_jacobian)`: True Jacobian. Our tests suggest that this is not very stable. Instead using `Broyden` with `Val(:true_jacobian)` gives faster and more reliable convergence.
      * `Val(:true_jacobian_diagonal)`: Diagonal of True Jacobian. This is a good choice for differentiable problems.
