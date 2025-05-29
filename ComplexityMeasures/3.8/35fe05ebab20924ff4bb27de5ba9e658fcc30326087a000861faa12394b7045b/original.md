```
outcome_space(o::OutcomeSpace, x) → Ω
```

Return a sorted container containing all *possible* outcomes of `o` for input `x`.

For some estimators the concrete outcome space is known without knowledge of input `x`, in which case the function dispatches to `outcome_space(o)`. In general it is recommended to use the 2-argument version irrespectively of estimator.
