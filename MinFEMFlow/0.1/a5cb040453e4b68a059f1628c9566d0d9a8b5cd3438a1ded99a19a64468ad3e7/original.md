```julia
copy_result!(
    target::MinFEMFlow.FlowSolver,
    origin::MinFEMFlow.FlowSolver
) -> Float64

```

Copies result from one flow solver to another. Does not check if problems in the solvers match.
