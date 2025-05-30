```julia
set_boundary_noslip!(
    fs::MinFEMFlow.FlowSolver,
    boundary::Union{Set{Int64}, Set{MinFEM.Boundary}}
) -> Missing

```

Updates no slip boundary and then invalidates the solution.
