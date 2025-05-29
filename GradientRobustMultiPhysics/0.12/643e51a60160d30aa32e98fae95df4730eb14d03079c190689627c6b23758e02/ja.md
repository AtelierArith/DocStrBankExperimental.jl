```julia
DiagonalOperator(
;
    ...
) -> GradientRobustMultiPhysics.DiagonalOperator{Float64}
DiagonalOperator(
    value::Real;
    name,
    onlynz,
    regions
) -> GradientRobustMultiPhysics.DiagonalOperator{<:Real}

```

*value*を指定された*regions*内のセルdofの対角エントリに配置します。

*onlyz*がtrueの場合、ゼロの値のみが変更されます。

PDE LHSでのみ適用可能です。
