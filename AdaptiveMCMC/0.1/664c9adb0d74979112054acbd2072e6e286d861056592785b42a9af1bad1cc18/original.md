```
r = AdaptiveMetropolis(x0; kwargs)
r = AdaptiveMetropolis(x0, [scale, [step]])
```

Constructor for AdaptiveMetropolis state.

# Arguments

  * `x0`: The initial state vector

# Keyword arguments

  * `scale`: Scaling parameter; default `2.38/sqrt(d)` where `d` is dimension.
  * `step`: Step size object; default `PolynomialStepSize(1.0)`
  * `S_init`: Initial proposal shape Cholesky factor; default `identity_cholesky(x0)`

If `s` is `RWMState`, then proposal samples may be drawn calling  `draw!(s, r)` and adaptation is performed with `adapt!(r, s)` or  `adapt_rb!(r, s, α)`.
