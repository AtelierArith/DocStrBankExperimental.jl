```
continuum_limit(prob::CellProblem,
    mesh_points=copy(prob.initial_condition);
    proliferation=false)
```

`FVMProblem`（右境界が固定されている場合）または `MBProblem`（右境界が自由な場合）を返し、これは [`CellProblem`](@ref) `prob` の連続体限界を定義します。引数 `mesh_points` は PDE 問題に使用するメッシュポイントを定義し、ポイントのグリッドまたは使用するポイントの数である可能性があります。問題が増殖を持つと見なされるべき場合は、`proliferation = true` に設定します。
