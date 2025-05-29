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

オペレーター O を与えられた FEMatrixBlock A に組み立て、A から FESpaces を使用します。
