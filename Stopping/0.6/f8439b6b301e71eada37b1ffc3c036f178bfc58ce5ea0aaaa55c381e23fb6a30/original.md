```
`unconstrained_check( :: AbstractNLPModel, :: NLPAtX; pnorm :: Real = Inf, kwargs...)`
```

Return the `pnorm`-norm of the gradient of the objective function.

Require `state.gx` (filled if not provided).

See also `optim_check_bounded`, `KKT`
