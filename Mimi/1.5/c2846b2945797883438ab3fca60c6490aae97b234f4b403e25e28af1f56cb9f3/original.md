```
connect_param!(obj::AbstractCompositeComponentDef, comp_def::AbstractComponentDef,
                param_name::Symbol, model_param_name::Symbol; check_attributes::Bool=true,
                ignoreunits::Bool = false)
```

Connect a parameter `param_name` in the component `comp_def` of composite `obj` to the model parameter `model_param_name`.
