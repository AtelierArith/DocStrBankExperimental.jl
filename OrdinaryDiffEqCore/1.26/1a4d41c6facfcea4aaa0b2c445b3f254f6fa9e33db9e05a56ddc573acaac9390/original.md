```
PIDController(beta1, beta2, beta3=zero(beta1);
              limiter=default_dt_factor_limiter,
              accept_safety=0.81)
```

The proportional-integral-derivative (PID) controller is a generalization of the [`PIController`](@ref) and can have improved stability and efficiency properties.

Construct a PID step size controller adapting the time step based on the formula

```
Δtₙ₊₁ = εₙ₊₁^(β₁/k) * εₙ^(β₂/k) * εₙ₋₁^(β₃/ k) * Δtₙ
```

where `k = min(alg_order, alg_adaptive_order) + 1` and `εᵢ` are inverses of the error estimates scaled by the tolerance (Söderlind, 2003). The step size factor is limited by the `limiter` with default value

```
limiter(x) = one(x) + atan(x - one(x))
```

as proposed by Söderlind and Wang (2006). A step will be accepted whenever the predicted step size change is bigger than `accept_safety`. Otherwise, the step is rejected and re-tried with the predicted step size.

Some standard controller parameters suggested in the literature are

| Controller | `beta1` | `beta2` | `beta3` |
|:---------- | -------:| -------:|:-------:|
| basic      |  `1.00` |  `0.00` |   `0`   |
| PI42       |  `0.60` | `-0.20` |   `0`   |
| PI33       |  `2//3` | `-1//3` |   `0`   |
| PI34       |  `0.70` | `-0.40` |   `0`   |
| H211PI     |  `1//6` |  `1//6` |   `0`   |
| H312PID    | `1//18` |  `1//9` | `1//18` |

!!! note
    In contrast to the [`PIController`](@ref), the coefficients `beta1, beta2, beta3` are scaled by the order of the method. Thus, standard controllers such as PI42 can use the same coefficients `beta1, beta2, beta3` for different algorithms.


!!! note
    In contrast to other controllers, the `PIDController` does not use the keyword arguments `qmin, qmax` to limit the step size change or the safety factor `gamma`. These common keyword arguments are replaced by the `limiter` and `accept_safety` to guarantee a smooth behavior (Söderlind and Wang, 2006). Because of this, a `PIDController` behaves different from a [`PIController`](@ref), even if `beta1, beta2` are adapted accordingly and `iszero(beta3)`.


## References

  * Söderlind (2003) Digital Filters in Adaptive Time-Stepping [DOI: 10.1145/641876.641877](https://doi.org/10.1145/641876.641877)
  * Söderlind, Wang (2006) Adaptive time-stepping and computational stability [DOI: 10.1016/j.cam.2005.03.008](https://doi.org/10.1016/j.cam.2005.03.008) # controller coefficients
  * Ranocha, Dalcin, Parsani, Ketcheson (2021) # history of the error estimates Optimized Runge-Kutta Methods with Automatic Step Size Control for   # accept a step if the predicted change of the step size Compressible Computational Fluid Dynamics    # is bigger than this parameter [arXiv:2104.06836](https://arxiv.org/abs/2104.06836)    # limiter of the dt factor (before clipping)
