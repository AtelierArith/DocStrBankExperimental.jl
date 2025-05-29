```julia
PDEDescription(
    name::String,
    nunknowns::Int64;
    algebraic,
    variables,
    unknown_names,
    equation_names
) -> GradientRobustMultiPhysics.PDEDescription

```

指定された数の未知数のための空のPDEDescriptionを作成します。
