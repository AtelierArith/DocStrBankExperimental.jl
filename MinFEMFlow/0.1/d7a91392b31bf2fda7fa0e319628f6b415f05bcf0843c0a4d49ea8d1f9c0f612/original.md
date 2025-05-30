```julia
set_boundary_inflow!(
    fs::MinFEMFlow.FlowSolver,
    boundary::Union{Set{Int64}, Set{MinFEM.Boundary}}
) -> Missing

```

Updates inflow boundary and then invalidates the solution.
