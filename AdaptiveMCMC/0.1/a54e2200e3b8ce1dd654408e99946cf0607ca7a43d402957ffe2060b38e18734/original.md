```
r = RobustAdaptiveMetropolis(x0; kwargs)
r = RobustAdaptiveMetropolis(x0, [acc_target, [step]])
```

Constructor for RobustAdaptiveMetropolis state.

# Arguments

  * `x0`: The initial state vector

# Keyword arguments

  * `acc_target`: Desired mean accept rate; default `0.234`.
  * `step`: Step size object; default `RAMStepSize(0.66,d)` where `d` is state dimension.
  * `S_init`: Initial proposal shape Cholesky factor; default `identity_cholesky(x0)`

If `s` is `RWMState`, then proposal samples may be drawn calling  `draw!(s, r)` and adaptation is performed with `adapt!(r, s, α)`.
