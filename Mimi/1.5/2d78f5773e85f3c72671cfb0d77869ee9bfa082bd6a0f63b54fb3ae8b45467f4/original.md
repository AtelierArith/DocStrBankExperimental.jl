```
set_param!(m::Model, comp_name::Symbol, param_name::Symbol, model_param_name::Symbol, value; dims=nothing)
```

Set the parameter `param_name` of a component `comp_name` in a model `m` to a given `value`,  storing the value in the model's parameter list by the provided name `model_param_name`. The `value` can by a scalar, an array, or a NamedAray. Optional keyword argument 'dims' is a list of the dimension names of the provided data, and will be used to check that they match the model's index labels.
