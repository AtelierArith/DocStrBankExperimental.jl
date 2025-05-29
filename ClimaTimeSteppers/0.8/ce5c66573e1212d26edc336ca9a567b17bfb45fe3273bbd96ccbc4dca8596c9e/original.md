```
ConvergenceCondition
```

An abstract type for objects that can check whether a sequence of non-negative scalar values `val[0], val[1], val[2], ...` has converged to some limit `L`, given the errors `err[iter] = |val[iter] - L|`.

Every subtype of `ConvergenceCondition` must define     `has_converged(::ConvergenceCondition, cache, val, err, iter)`. The `cache`, which is set to `nothing` by default, may be used to store information from previous iterations that is useful for determining convergence. In order to have access to a `cache` of some particular type, a subtype of `ConvergenceCondition` should define     `cache_type(::ConvergenceCondition, ::Type{FT})`. To specify on which iterations this cache should be updated, it should define     `needs_cache_update(::ConvergenceCondition, iter)`. To specify how the cache should be update on those iterations, it should define     `updated_cache(::ConvergenceCondition, cache, val, err, iter)`.

Although `cache_type` can call `promote_type` to prevent potential type instability errors, this should be avoided in order to ensure that users write type-stable code.
