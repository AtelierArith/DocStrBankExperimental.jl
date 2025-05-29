```
StopWhenResidualIsReducedByFactorOrPower <: StoppingCriterion
```

A functor for testing if the norm of residual at the current iterate is reduced either by a power of 1+θ or by a factor κ compared to the norm of the initial residual. The criterion hence reads

$\lVert r_k \rVert_{p} ≦ \lVert r_0 \rVert_{p^{(0)}} \min \bigl( κ, \lVert r_0 \rVert_{p^{(0)}}  \bigr)$.

# Fields

  * `κ`:      the reduction factor
  * `θ`:      part of the reduction power
  * `at_iteration::Int`: an integer indicating at which the stopping criterion last indicted to stop, which might also be before the solver started (`0`). Any negative value indicates that this was not yet the case;

# Constructor

```
StopWhenResidualIsReducedByFactorOrPower(; κ=0.1, θ=1.0)
```

Initialize the StopWhenResidualIsReducedByFactorOrPower functor to indicate to stop after the norm of the current residual is lesser than either the norm of the initial residual to the power of 1+θ or the norm of the initial residual times κ.

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
