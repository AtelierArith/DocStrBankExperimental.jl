```
DebugGradientChange()
```

debug for the amount of change of the gradient (stored in `get_gradient(o)` of the [`AbstractManoptSolverState`](@ref) `o`) during the last iteration. See [`DebugEntryChange`](@ref) for the general case

# Keyword parameters

  * `storage`: (`StoreStateAction( (:Gradient,) )`) storage of the action for previous data
  * `prefix`:  (`"Last Change:"`) prefix of the debug output (ignored if you set `format`)
  * `io`:      (`stdout`) default stream to print the debug to.
  * `format`:  ( `"$prefix %f"`) format to print the output
