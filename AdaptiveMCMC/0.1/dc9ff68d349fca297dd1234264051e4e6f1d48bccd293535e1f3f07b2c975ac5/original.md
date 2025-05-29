```
r = AdaptiveScalingWithinAdaptiveMetropolis(x0; kwargs)
r = AdaptiveScalingWithinAdaptiveMetropolis(x0, [acc_target, 
      [scale, [stepAM, [stepASM]]]])
```

Constructor for AdaptiveScalingWithinAdaptiveMetropolis state.

# Arguments

  * `x0`: The initial state vector.

# Keyword arguments

  * `acc_target`: Desired mean accept rate; default `0.234`.
  * `scale`: Initial scaling; default `2.38/sqrt(d)` where `d` is the dimension.
  * `stepAM`: Step size object for covariance adaptation;            default `PolynomialStepSize(0.66)`.
  * `stepASM`: Step size object for scaling adaptation;            default `PolynomialStepSize(0.66)`.

If `s` is `RWMState`, then proposal samples may be drawn calling  `draw!(s, r)` and adaptation is performed with `adapt!(r, s, α)` or  `adapt_rb!(r, s, α)`.
