```julia
set_inflow!(
    fs::MinFEMFlow.FlowSolver,
    inflow::Union{Function, Vector{Float64}}
) -> Missing

```

流入関数を更新し、その後解を無効にします。
