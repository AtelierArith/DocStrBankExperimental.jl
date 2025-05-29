```
set_optimizer_model_ready(model::InfiniteModel, status::Bool)
```

Set the status of the optimizer model to whether it is up to date or not. Note is more intended as an internal function, but is useful for extensions.

**Example**

```julia-repl
julia> set_optimizer_model_ready(model, true)

julia> optimizer_model_ready(model)
true
```
