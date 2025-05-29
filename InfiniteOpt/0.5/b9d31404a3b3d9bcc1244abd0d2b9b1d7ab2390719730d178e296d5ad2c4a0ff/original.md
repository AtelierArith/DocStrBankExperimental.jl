```
optimizer_model_key(model::JuMP.Model)::Any
```

Return the extension key used in the optimizer model `model`. Errors if `model.ext` contains more than one key. This is intended for internal use and extensions. For extensions this is used to dispatch to the appropriate optmizer model functions such as extensions to [`build_optimizer_model!`](@ref). This is intended as an internal method. See  [`optimizer_model_key`](@ref optimizer_model_key(::InfiniteModel))  for the public method
