```
set_param!(md::ModelDef, comp_name::Symbol, param_name::Symbol, value; dims=nothing)
```

Set the value of parameter `param_name` in component `comp_name` of Model Def `md`  to `value`.  This will create a shared model parameter with name `param_name`  and connect `comp_name`'s parameter `param_name` to it.

The `value` can by a scalar, an array, or a NamedAray. Optional keyword argument 'dims' is a list of the dimension names of the provided data, and will be used to check that they match the model's index labels.
