```julia
assemble_operator!(
    A::GradientRobustMultiPhysics.FEMatrixBlock,
    O::GradientRobustMultiPhysics.PDEOperator;
    ...
) -> Any
assemble_operator!(
    A::GradientRobustMultiPhysics.FEMatrixBlock,
    O::GradientRobustMultiPhysics.PDEOperator,
    CurrentSolution::Union{Nothing, GradientRobustMultiPhysics.FEVector};
    Pattern,
    skip_preps,
    time,
    At
) -> Any

```

与えられた FEMatrixBlock A に FESpaces を使用して演算子 O を組み立てます。
