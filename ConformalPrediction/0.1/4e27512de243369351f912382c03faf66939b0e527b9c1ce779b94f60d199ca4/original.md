```
conformal_model(model::Supervised; method::Union{Nothing, Symbol}=nothing, kwargs...)
```

A simple wrapper function that turns a `model::Supervised` into a conformal model. It accepts an optional key argument that can be used to specify the desired `method` for conformal prediction as well as additinal `kwargs...` specific to the `method`.
