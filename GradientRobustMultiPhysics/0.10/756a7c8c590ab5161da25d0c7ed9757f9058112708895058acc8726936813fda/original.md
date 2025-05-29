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

assembles the operator O into the given FEMatrixBlock A using FESpaces from A.
