```
disconnect_param!(obj::AbstractCompositeComponentDef, comp_name::Symbol, param_name::Symbol)
```

Remove any parameter connections for a given parameter `param_name` in a given component `comp_def` which must be a direct subcomponent of composite `obj`.
