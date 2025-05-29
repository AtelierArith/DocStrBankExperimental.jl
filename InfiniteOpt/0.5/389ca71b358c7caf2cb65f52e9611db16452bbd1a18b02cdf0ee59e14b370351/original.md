```
add_infinite_model_optimizer(opt_model::JuMP.Model, inf_model::InfiniteModel)
```

Parse the current optimizer and its attributes associated with `inf_model` and load them into `opt_model`. This is intended to be used as an internal method for [`set_optimizer_model`](@ref).
