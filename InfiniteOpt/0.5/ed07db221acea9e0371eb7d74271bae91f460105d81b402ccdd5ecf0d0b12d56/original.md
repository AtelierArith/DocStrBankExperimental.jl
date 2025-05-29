```
optimizer_model_key(model::InfiniteModel)::Any
```

Return the extension key used in the optimizer model of `model`. Errors if `optimizer_model.ext` contains more than one key. This is intended for internal use and extensions. For extensions this is used to dispatch to the appropriate optmizer model functions such as extensions to [`build_optimizer_model!`](@ref).

**Example**

```julia-repl
julia> optimizer_model_key(model)
:TransData
```
