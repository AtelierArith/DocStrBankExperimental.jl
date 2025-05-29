```
clear_optimizer_model_build!(model::JuMP.Model)::JuMP.Model
```

Empty the optimizer model using appropriate calls of `Base.empty!`. This effectively resets `model` except the optimizer, its attributes, and an an emptied optimizer model data struct are maintained. This is intended as an internal method for use by [`build_optimizer_model!`](@ref).
