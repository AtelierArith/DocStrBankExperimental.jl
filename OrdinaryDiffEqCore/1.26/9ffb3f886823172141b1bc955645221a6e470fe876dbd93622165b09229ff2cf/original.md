```
IController()
```

The standard (integral) controller is the most basic step size controller. This controller is usually the first one introduced in numerical analysis classes but should only be used rarely in practice because of efficiency problems for many problems/algorithms.

Construct an integral (I) step size controller adapting the time step based on the formula

```
Δtₙ₊₁ = εₙ₊₁^(1/k) * Δtₙ
```

where `k = get_current_adaptive_order(alg, integrator.cache) + 1` and `εᵢ` is the inverse of the error estimate `integrator.EEst` scaled by the tolerance (Hairer, Nørsett, Wanner, 2008, Section II.4). The step size factor is multiplied by the safety factor `gamma` and clipped to the interval `[qmin, qmax]`. A step will be accepted whenever the estimated error `integrator.EEst` is less than or equal to unity. Otherwise, the step is rejected and re-tried with the predicted step size.

## References

  * Hairer, Nørsett, Wanner (2008) Solving Ordinary Differential Equations I Nonstiff Problems [DOI: 10.1007/978-3-540-78862-1](https://doi.org/10.1007/978-3-540-78862-1)
