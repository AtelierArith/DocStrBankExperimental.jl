```julia
struct LocalScope <: ModelingToolkit.SymScope
```

The default scope of a variable. It belongs to the system whose equations it is involved in and is namespaced by every level of the hierarchy.
