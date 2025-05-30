```
StokesFlowSolver(
    mesh::Mesh,
    inflow_boundary::Union{Set{Boundary}, Set{Int64}},
    noslip_boundary::Union{Set{Boundary}, Set{Int64}},
    inflow::Union{Vector{Float64}, Function};
    verbose::Bool = true
) -> FlowSolver
```

Stokes流の解法ルーチンを表すFlowSolverオブジェクトを返します。
