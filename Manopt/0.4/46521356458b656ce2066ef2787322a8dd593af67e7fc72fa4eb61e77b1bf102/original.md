```
DebugChange(M=DefaultManifold())
```

debug for the amount of change of the iterate (stored in `get_iterate(o)` of the [`AbstractManoptSolverState`](@ref)) during the last iteration. See [`DebugEntryChange`](@ref) for the general case

# Keyword parameters

  * `storage`:                   (`StoreStateAction( [:Gradient] )` storage of the previous action
  * `prefix`:                    (`"Last Change:"`) prefix of the debug output (ignored if you set `format`)
  * `io`:                        (`stdout`) default stream to print the debug to.
  * `format`:                    ( `"$prefix %f"`) format to print the output.
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M)`) the inverse retraction to be used for approximating distance.
