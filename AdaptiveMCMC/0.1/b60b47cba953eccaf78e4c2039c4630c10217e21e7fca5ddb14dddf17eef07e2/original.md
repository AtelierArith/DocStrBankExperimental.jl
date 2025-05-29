```
r = AdaptiveScalingMetropolis(x0; kwargs)
r = AdaptiveScalingMetropolis(x0, [acc_target, [scale, [step]]])
r = AdaptiveScalingMetropolis(acc_target, scale, step)
```

Constructor for AdaptiveScalingMetropolis state.

# Arguments

  * `x0`: The initial state vector (not used).

# Keyword arguments

  * `acc_target`: Desired mean accept rate; default `0.44` for   univariate and `0.234` for multivariate.
  * `scale`: Initial scaling; default `1.0`.
  * `step`: Step size object; default `PolynomialStepSize(0.66)`.

If `s` is `RWMState`, then proposal samples may be drawn calling  `draw!(s, r)` and adaptation is performed with `adapt!(r, s, α)`.
