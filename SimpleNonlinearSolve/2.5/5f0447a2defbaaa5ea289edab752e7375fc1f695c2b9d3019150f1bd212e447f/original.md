```
SimpleTrustRegion(;
    autodiff = AutoForwardDiff(), max_trust_radius = 0.0,
    initial_trust_radius = 0.0, step_threshold = nothing,
    shrink_threshold = nothing, expand_threshold = nothing,
    shrink_factor = 0.25, expand_factor = 2.0, max_shrink_times::Int = 32,
    nlsolve_update_rule = Val(false)
)
```

A low-overhead implementation of a trust-region solver. This method is non-allocating on scalar and static array problems.

### Keyword Arguments

  * `autodiff`: determines the backend used for the Jacobian. Defaults to `nothing` (i.e. automatic backend selection). Valid choices include jacobian backends from `DifferentiationInterface.jl`.
  * `max_trust_radius`: the maximum radius of the trust region. Defaults to `max(norm(f(u0)), maximum(u0) - minimum(u0))`.
  * `initial_trust_radius`: the initial trust region radius. Defaults to `max_trust_radius / 11`.
  * `step_threshold`: the threshold for taking a step. In every iteration, the threshold is compared with a value `r`, which is the actual reduction in the objective function divided by the predicted reduction. If `step_threshold > r` the model is not a good approximation, and the step is rejected. Defaults to `0.0001`. For more details, see [Rahpeymaii, F.](https://link.springer.com/article/10.1007/s40096-020-00339-4)
  * `shrink_threshold`: the threshold for shrinking the trust region radius. In every iteration, the threshold is compared with a value `r` which is the actual reduction in the objective function divided by the predicted reduction. If `shrink_threshold > r` the trust region radius is shrunk by `shrink_factor`. Defaults to `0.25`. For more details, see [Rahpeymaii, F.](https://link.springer.com/article/10.1007/s40096-020-00339-4)
  * `expand_threshold`: the threshold for expanding the trust region radius. If a step is taken, i.e `step_threshold < r` (with `r` defined in `shrink_threshold`), a check is also made to see if `expand_threshold < r`. If that is true, the trust region radius is expanded by `expand_factor`. Defaults to `0.75`.
  * `shrink_factor`: the factor to shrink the trust region radius with if `shrink_threshold > r` (with `r` defined in `shrink_threshold`). Defaults to `0.25`.
  * `expand_factor`: the factor to expand the trust region radius with if `expand_threshold < r` (with `r` defined in `shrink_threshold`). Defaults to `2.0`.
  * `max_shrink_times`: the maximum number of times to shrink the trust region radius in a row, `max_shrink_times` is exceeded, the algorithm returns. Defaults to `32`.
  * `nlsolve_update_rule`: If set to `Val(true)`, updates the trust region radius using the update rule from NLSolve.jl. Defaults to `Val(false)`. If set to `Val(true)`, few of the radius update parameters – `step_threshold = 0.05`, `expand_threshold = 0.9`, and `shrink_factor = 0.5` – have different defaults.
