```julia
struct DelayParentScope <: ModelingToolkit.SymScope
```

Denotes that a variable belongs to a system that is at least `N + 1` levels up in the hierarchy from the system whose equations it is involved in. It is namespaced by the first `N` parents and not namespaced by the `N+1`th parent in the hierarchy. The scope of the variable after this point is given by `parent`.

In other words, this scope delays applying `ParentScope` by `N` levels, and applies `LocalScope` in the meantime.

# Fields

  * `parent::ModelingToolkit.SymScope`
  * `N::Int64`
