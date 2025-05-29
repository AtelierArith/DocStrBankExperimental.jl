```
StopWhenResidualIsReducedByFactorOrPower <: StoppingCriterion
```

A functor for testing if the norm of residual at the current iterate is reduced either by a power of 1+θ or by a factor κ compared to the norm of the initial residual. The criterion hence reads $\Vert r_k \Vert_p \leqq \Vert r_0 \Vert_p \min \bigl( \kappa, \Vert r_0 \Vert_p^θ \bigr)$.

# Fields

  * `κ`:      the reduction factor
  * `θ`:      part of the reduction power
  * `reason`: stores a reason of stopping if the stopping criterion has one be reached, see [`get_reason`](@ref).

# Constructor

```
StopWhenResidualIsReducedByFactorOrPower(; κ=0.1, θ=1.0)
```

Initialize the StopWhenResidualIsReducedByFactorOrPower functor to indicate to stop after the norm of the current residual is lesser than either the norm of the initial residual to the power of 1+θ or the norm of the initial residual times κ.

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
