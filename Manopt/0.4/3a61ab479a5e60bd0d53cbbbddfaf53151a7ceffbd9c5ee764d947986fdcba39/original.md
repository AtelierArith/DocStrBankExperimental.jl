```
DebugPrimalResidual <: DebugAction
```

A Debug action to print the primal residual. The constructor accepts a printing function and some (shared) storage, which should at least record `:Iterate`, `:X` and `:n`.

# Constructor

```
DebugPrimalResidual()
```

with the keywords

  * `io` (`stdout`) - stream to perform the debug to
  * format (`"$prefix%s"`) format to print the dual residual, using the
  * `prefix` (`"Primal Residual: "`) short form to just set the prefix
  * `storage` (a new [`StoreStateAction`](@ref)) to store values for the debug.
