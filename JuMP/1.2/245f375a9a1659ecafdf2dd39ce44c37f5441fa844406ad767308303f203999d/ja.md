```
build_constraint(
    _error::Function,
    f::AbstractVector{<:AbstractJuMPScalar},
    s::MOI.GreaterThan,
    extra::Union{MOI.AbstractVectorSet,AbstractVectorSet},
)
```

ヘルパーメソッドで、次のように書き換えます。

```julia
@constraint(model, X >= Y, extra)
```

を

```julia
@constraint(model, X - Y in extra)
```
