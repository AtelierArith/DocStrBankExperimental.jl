```
variable_dimensions(obj::AbstractCompositeComponentDef, comp_path::ComponentPath, var_name::Symbol)
```

Return the names of the dimensions of variable `var_name` exposed in the composite component definition indicated by`obj` along the component path `comp_path`. The `comp_path` is of type `Mimi.ComponentPath` with the single field being an NTuple of symbols describing the relative (to a composite) or absolute (relative to ModelDef) path through composite nodes to specific composite or leaf node.
