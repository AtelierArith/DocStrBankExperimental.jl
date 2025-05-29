```
build_constraint(
    _error::Function,
    f::AbstractVector{<:AbstractJuMPScalar},
    s::MOI.LessThan,
    extra::Union{MOI.AbstractVectorSet,AbstractVectorSet},
)
```

ヘルパーメソッドで、次のように書き換えます。

```julia
@constraint(model, Y <= X, extra)
```

を

```julia
@constraint(model, X - Y in extra)
```
