```
`KKT( :: AbstractNLPModel, :: NLPAtX; pnorm :: Real = Inf, kwargs...)`
```

Check the KKT conditions.

Note: `state.gx` is mandatory + if bounds `state.mu` + if constraints `state.cx`, `state.Jx`, `state.lambda`.

See also `unconstrained_check`, `optim_check_bounded`
