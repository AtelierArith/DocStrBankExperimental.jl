```julia
set_inflow!(
    fs::MinFEMFlow.FlowSolver,
    inflow::Union{Function, Vector{Float64}}
) -> Missing

```

Updates inflow function and then invalidates the solution.
