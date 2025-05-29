```
build_optimizer_model!(model::InfiniteModel, key::Val{ext_key_name};
                       [kwargs...])
```

Build the optimizer model stored in `model` such that it can be treated as a normal JuMP model, where the `Model.ext` field contains a key that points to a datastructure that appropriately maps the data between the two models. The key argument should be be typed to `Val{ext_key_name}`. This should also use [`clear_optimizer_model_build!`](@ref) to empty the out the current optimizer model. Ultimately, [`set_optimizer_model`](@ref) should be called to insert the build optimizer model into `model` and [`set_optimizer_model_ready`](@ref) should be used to update the optimizer model's status.
