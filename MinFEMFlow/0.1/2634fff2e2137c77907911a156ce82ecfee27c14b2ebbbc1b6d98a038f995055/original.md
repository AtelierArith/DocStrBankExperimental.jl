```
StokesFlowSolver(
    mesh::Mesh,
    inflow_boundary::Union{Set{Boundary}, Set{Int64}},
    noslip_boundary::Union{Set{Boundary}, Set{Int64}},
    inflow::Union{Vector{Float64}, Function};
    verbose::Bool = true
) -> FlowSolver
```

Returns FlowSolver object representing the solution routine for a Stokes flow.
