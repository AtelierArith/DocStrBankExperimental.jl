```
variable_dimensions(obj::AbstractCompositeComponentDef, comp::Symbol, var_name::Symbol)
```

Return the names of the dimensions of variable `var_name` exposed in the composite component definition indicated by `obj` along the component path `comp_path`. The `comp_path` is a tuple of symbols describing the relative (to a composite) or absolute (relative to ModelDef) path through composite nodes to specific composite or leaf node.
