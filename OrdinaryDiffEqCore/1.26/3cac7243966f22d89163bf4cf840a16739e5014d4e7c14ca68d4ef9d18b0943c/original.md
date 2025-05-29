```
PIController(beta1, beta2)
```

The proportional-integral (PI) controller is a widespread step size controller with improved stability properties compared to the [`IController`](@ref). This controller is the default for most algorithms in OrdinaryDiffEq.jl.

Construct a PI step size controller adapting the time step based on the formula

```
Δtₙ₊₁ = εₙ₊₁^β₁ * εₙ^β₂ * Δtₙ
```

where `εᵢ` are inverses of the error estimates scaled by the tolerance (Hairer, Nørsett, Wanner, 2010, Section IV.2). The step size factor is multiplied by the safety factor `gamma` and clipped to the interval `[qmin, qmax]`. A step will be accepted whenever the estimated error `integrator.EEst` is less than or equal to unity. Otherwise, the step is rejected and re-tried with the predicted step size.

!!! note
    The coefficients `beta1, beta2` are not scaled by the order of the method, in contrast to the [`PIDController`](@ref). For the `PIController`, this scaling by the order must be done when the controller is constructed.


## References

  * Hairer, Nørsett, Wanner (2010) Solving Ordinary Differential Equations II Stiff and Differential-Algebraic Problems [DOI: 10.1007/978-3-642-05221-7](https://doi.org/10.1007/978-3-642-05221-7)
  * Hairer, Nørsett, Wanner (2008) Solving Ordinary Differential Equations I Nonstiff Problems [DOI: 10.1007/978-3-540-78862-1](https://doi.org/10.1007/978-3-540-78862-1)
