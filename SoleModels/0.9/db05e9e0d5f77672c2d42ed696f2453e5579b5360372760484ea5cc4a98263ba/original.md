```
outputtype(m::AbstractModel)
```

Return a supertype for the outputs obtained when `apply`ing a model.

# Implementation

The result depends on whether the model is incomplete or complete

```julia-repl
julia> outputtype(m::AbstractModel{O}) where {O} = iscomplete(m) ? O : Union{Nothing,O}
```

Note that if the model is complete, then `outputtype(m)` is equal to `outcometype(m)`.

See also [`AbstractModel`](@ref), [`apply`](@ref), [`iscomplete`](@ref), [`outcometype`](@ref).
