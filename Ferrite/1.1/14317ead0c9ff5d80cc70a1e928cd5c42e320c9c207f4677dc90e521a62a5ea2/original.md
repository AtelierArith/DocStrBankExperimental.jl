```
update!(ch::ConstraintHandler, time::Real=0.0)
```

Update time-dependent inhomogeneities for the new time. This calls `f(x)` or `f(x, t)` when applicable, where `f` is the function(s) corresponding to the constraints in the handler, to compute the inhomogeneities.

Note that this is called implicitly in `close!(::ConstraintHandler)`.
