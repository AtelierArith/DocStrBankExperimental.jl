```
build_constraint(
    _error::Function,
    f::AbstractVector{<:AbstractJuMPScalar},
    s::MOI.LessThan,
    extra::Union{MOI.AbstractVectorSet,AbstractVectorSet},
)
```

A helper method that re-writes

```julia
@constraint(model, Y <= X, extra)
```

into

```julia
@constraint(model, X - Y in extra)
```
