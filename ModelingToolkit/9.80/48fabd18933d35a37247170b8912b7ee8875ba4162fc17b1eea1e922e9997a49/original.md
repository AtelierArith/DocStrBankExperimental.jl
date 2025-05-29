```julia
struct GlobalScope <: ModelingToolkit.SymScope
```

Denotes that a variable belongs to the root system in the hierarchy, regardless of which equations of subsystems in the hierarchy it is involved in. Variables with this scope are never namespaced and only added to the unknowns/parameters of a system when calling `complete` or `structural_simplify`.
