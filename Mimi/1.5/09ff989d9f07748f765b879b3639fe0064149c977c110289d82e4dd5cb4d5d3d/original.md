```
set_param!(md::ModelDef, param_name::Symbol, value; dims=nothing)
```

Set the value of parameter `param_name in all components of the Model Def`md`that have a parameter of the specified name to`value`.  This will create a shared model parameter with name`param_name` and connect all component parameters with that name to it.

The `value` can by a scalar, an array, or a NamedAray. Optional keyword argument 'dims' is a list of the dimension names of the provided data, and will be used to check that they match the model's index labels.
