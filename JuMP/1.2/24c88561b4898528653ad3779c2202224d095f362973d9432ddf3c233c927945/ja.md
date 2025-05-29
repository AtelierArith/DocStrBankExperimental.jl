```
build_constraint(
    _error::Function,
    Q::AbstractMatrix{<:AbstractJuMPScalar},
    ::PSDCone,
)
```

`Q`が対称かつ半正定値であることを制約する[`SquareMatrixShape`](@ref)の形状の`VectorConstraint`を返します。

この関数は、次のように[`@constraint`](@ref)マクロによって使用されます：

```julia
@constraint(model, Q in PSDCone())
```
