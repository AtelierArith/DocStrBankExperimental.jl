```
`optim_check_bounded( :: AbstractNLPModel, :: NLPAtX; pnorm :: Real = Inf, kwargs...)`
```

Check the `pnorm`-norm of the gradient of the objective function projected over the bounds.

Require `state.gx` (filled if not provided).

See also `unconstrained_check`, `KKT`
