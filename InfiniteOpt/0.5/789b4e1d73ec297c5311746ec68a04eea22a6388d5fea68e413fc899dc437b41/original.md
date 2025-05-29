```
build_optimizer_model!(model::InfiniteModel; [kwargs...])
```

Build the optimizer model stored in `model` such that it can be treated as a normal JuMP model. Specifically, translate the variables and constraints stored in `model` into ones that are stored in the optimizer model and can be solved. This is provided generally to accomodate extensions that use custom optimizer model types in accordance with [`optimizer_model_key`](@ref). However, it may be useful in certain applications when the user desires to force a build without calling `optimize!`. Extensions will need to implement their own version of the function `build_optimizer_model!(model::InfiniteModel, key::Val{ext_key_name}; kwargs...)`.

**Example**

```julia-repl
julia> build_optimizer_model!(model)

julia> optimizer_model_ready(model)
true
```
