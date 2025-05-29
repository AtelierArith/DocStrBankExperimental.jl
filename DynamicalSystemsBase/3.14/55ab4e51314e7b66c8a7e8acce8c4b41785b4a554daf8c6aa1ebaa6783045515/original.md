```
set_state!(ds::DynamicalSystem, mapping::AbstractDict)
```

Convenience version of `set_state!` that iteratively calls `set_state!(ds, val, i)` for all index-value pairs `(i, val)` in `mapping`. This is useful primarily in two cases:

1. to partially set only some state variables,
2. to set variables by name (if the system is created via ModelingToolkit.jl)

so that you don't have to keep track of the order of the dynamic variables.
