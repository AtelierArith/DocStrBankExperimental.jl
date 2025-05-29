```
DebugChange(M=DefaultManifold(); kwargs...)
```

debug for the amount of change of the iterate (stored in `get_iterate(o)` of the [`AbstractManoptSolverState`](@ref)) during the last iteration. See [`DebugEntryChange`](@ref) for the general case

# Keyword parameters

  * `storage=`[`StoreStateAction`](@ref)`( [:Gradient] )` storage of the previous action
  * `prefix="Last Change:"`: prefix of the debug output (ignored if you set `format`)
  * `io=stdout`: default stream to print the debug to.
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)

the inverse retraction   to be used for approximating distance.
