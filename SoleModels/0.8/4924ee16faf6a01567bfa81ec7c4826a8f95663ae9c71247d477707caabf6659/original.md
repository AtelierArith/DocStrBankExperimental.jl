```
outputtype(m::AbstractModel)
```

Return a supertype for the outputs obtained when `apply`ing a model. The result depends on whether the model is open or closed:

```
outputtype(M::AbstractModel{O}) = isopen(M) ? Union{Nothing,O} : O
```

Note that if the model is closed, then `outputtype(m)` is equal to `outcometype(m)`.

See also [`isopen`](@ref), [`apply`](@ref), [`outcometype`](@ref), [`AbstractModel`](@ref).
