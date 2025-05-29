```
outcometype(::Type{<:AbstractModel{O}}) where {O} = O
outcometype(m::AbstractModel) = outcometype(typeof(m))
```

Return the outcome type of a model (type).

See also [`AbstractModel`](@ref).
