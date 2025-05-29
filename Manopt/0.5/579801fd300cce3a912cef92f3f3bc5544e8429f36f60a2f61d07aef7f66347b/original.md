```
DebugPrimalDualResidual <: DebugAction
```

A Debug action to print the primal dual residual. The constructor accepts a printing function and some (shared) storage, which should at least record `:Iterate`, `:X` and `:n`.

# Constructor

```
DebugPrimalDualResidual()
```

with the keywords

# Keyword warguments

  * `io=`stdout`: stream to perform the debug to
  * `format="$prefix%s"`: format to print the dual residual, using the
  * `prefix="PD Residual: "`: short form to just set the prefix
  * `storage` (a new [`StoreStateAction`](@ref)) to store values for the debug.
