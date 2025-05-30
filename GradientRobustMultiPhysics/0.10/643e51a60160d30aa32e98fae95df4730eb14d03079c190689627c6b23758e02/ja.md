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

は、指定された *regions* 内のセルの自由度の対角エントリに *value* を配置します。

*onlyz* が true の場合、ゼロの値のみが変更されます。

PDE LHS にのみ適用できます。
