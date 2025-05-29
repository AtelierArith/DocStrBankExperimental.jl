```
SymbolicdModel(DM::Union{AbstractDataModel,ModelMap}; sub::Bool=true)
```

Produces `String` of symbolic expression for the model map if possible.

Kwarg `sub` controls whether the given variable names are taken from `DM` (`sub=true`) or whether generic variable names, e.g. `θ[1]` are used (`sub=false`) for better copyability.
