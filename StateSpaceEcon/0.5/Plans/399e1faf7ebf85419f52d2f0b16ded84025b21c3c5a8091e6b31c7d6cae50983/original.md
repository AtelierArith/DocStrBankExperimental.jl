```
exog_endo!(plan, exog_vars, endo_vars, date)
```

Modify the given plan so that the given variables listed in `exog_vars` will be exogenous and the variables listed in `endo_vars` will be endogenous on the given dates. `exog_vars` and `endo_vars` can each be a `Symbol` or a `String` or a `Vector` of such. `date` can be a moment in time (same type as the plan), or a range or an iterable or a container.
