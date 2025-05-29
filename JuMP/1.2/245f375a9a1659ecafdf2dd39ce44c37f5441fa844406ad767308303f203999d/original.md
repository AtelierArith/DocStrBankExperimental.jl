```
build_constraint(
    _error::Function,
    f::AbstractVector{<:AbstractJuMPScalar},
    s::MOI.GreaterThan,
    extra::Union{MOI.AbstractVectorSet,AbstractVectorSet},
)
```

A helper method that re-writes

```julia
@constraint(model, X >= Y, extra)
```

into

```julia
@constraint(model, X - Y in extra)
```
