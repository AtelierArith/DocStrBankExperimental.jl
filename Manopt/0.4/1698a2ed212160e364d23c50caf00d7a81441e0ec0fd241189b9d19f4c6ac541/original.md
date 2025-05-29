```
DebugDualResidual <: DebugAction
```

A Debug action to print the dual residual. The constructor accepts a printing function and some (shared) storage, which should at least record `:Iterate`, `:X` and `:n`.

# Constructor

DebugDualResidual()

with the keywords

  * `io` (`stdout`) - stream to perform the debug to
  * format (`"$prefix%s"`) format to print the dual residual, using the
  * `prefix` (`"Dual Residual: "`) short form to just set the prefix
  * `storage` (a new [`StoreStateAction`](@ref)) to store values for the debug.
