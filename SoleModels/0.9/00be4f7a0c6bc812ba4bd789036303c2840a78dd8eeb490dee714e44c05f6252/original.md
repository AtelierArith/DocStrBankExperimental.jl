```
iscomplete(::AbstractModel)::Bool
```

Return whether a model is complete.

An [`AbstractModel`](@ref) is *complete* if it is always able to provide an outcome of type `O`. Otherwise, the model can output `nothing` values and is referred to as *incomplete*.

[`Rule`](@ref) is an example of an *incomplete* model, while [`Branch`](@ref) is an example of *complete* model.

See also [`AbstractModel`](@ref).
