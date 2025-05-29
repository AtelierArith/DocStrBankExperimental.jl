```
pirls!(m::GeneralizedLinearMixedModel)
```

Use Penalized Iteratively Reweighted Least Squares (PIRLS) to determine the conditional modes of the random effects.

When `varyβ` is true both `u` and `β` are optimized with PIRLS.  Otherwise only `u` is optimized and `β` is held fixed.

Passing `verbose = true` provides verbose output of the iterations.
