```
test_scalar(f, z; rtol=1e-9, atol=1e-9, fdm=central_fdm(5, 1), fkwargs=NamedTuple(), check_inferred=true, kwargs...)
```

Given a function `f` with scalar input and scalar output, perform finite differencing checks, at input point `z` to confirm that there are correct `frule` and `rrule`s provided.

# Arguments

  * `f`: function for which the `frule` and `rrule` should be tested.
  * `z`: input at which to evaluate `f` (should generally be set to an arbitrary point in the domain).

# Keyword Arguments

  * `fdm`: the finite differencing method to use.
  * `fkwargs` are passed to `f` as keyword arguments.
  * If `check_inferred=true`, then the inferrability (type-stability) of the `frule` and `rrule` are checked.
  * `testset_name`: if provided, the name of the testset used to wrap the tests. Otherwise it is determined from the function and argument types.
  * All remaining keyword arguments are passed to `isapprox`.
