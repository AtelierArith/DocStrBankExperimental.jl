```julia
set_boundary_inflow!(
    fs::MinFEMFlow.FlowSolver,
    boundary::Union{Set{Int64}, Set{MinFEM.Boundary}}
) -> Missing

```

流入境界を更新し、その後解を無効にします。
