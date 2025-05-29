```julia
struct ParentScope <: ModelingToolkit.SymScope
```

Denotes that the variable does not belong to the system whose equations it is involved in. It is not namespaced by this system. In the immediate parent of this system, the scope of this variable is given by `parent`.

# Fields

  * `parent::ModelingToolkit.SymScope`
