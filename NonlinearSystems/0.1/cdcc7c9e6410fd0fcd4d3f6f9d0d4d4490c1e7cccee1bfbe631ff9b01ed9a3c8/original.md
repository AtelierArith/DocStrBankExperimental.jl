```
HybridSolver(fdf::OnceDifferentiable, x, fx, J, P; kwargs...)
```

Construct `HybridSolver` for solving a problem of type `P` with [`Hybrid`](@ref) method. Users are not expected to call this method directly but should pass keyword arguments to `init` or `solve` instead. See also [`Hybrid`](@ref).

# Keywords

  * `linsolver=default_linsolver(fdf, x0, P)`: solver for the underlying linear problems.
  * `factor_init::Real=1.0`: a factor for scaling the initial trust region radius.
  * `factor_up::Real=2.0`: a factor for expanding the trust region radius.
  * `factor_down::Real=0.5`: a factor for shrinking the trust region radius.
  * `scaling::Bool=true`: allow improving the scaling of trust region.
  * `rank1update::Bool=true`: allow using rank-1 update for the Jacobian matrix and factorization.
  * `thres_jac::Integer=2`: recompute the Jacobian matrix if the trust region is shrinked consecutively by the specified number of times; setting a non-positive value results in recomputing the Jacobian matrix after each step.
  * `thres_nslow1::Integer=10`: signal slow solver progress if the reduction in residual norm remains small for the specified number of consecutive steps.
  * `thres_nslow2::Integer=5`: signal slow solver progress if there is no expansion of trust region after recomputing the Jacobian matrix in the specified number of consecutive steps.
  * `warn::Bool=true`: print a warning message for slow solver progress
