```
set_default_solver_view!(model, modeldata)
```

（オプションで、全体モデルのために `modeldata.solver_view_all` を [`SolverView`](@ref) に設定し、`modeldata.hostdep_data` を任意の非状態変数ホスト依存変数に設定します）

`reallocate_hostdep_eltype` は、`hostdep_data` を再割り当てするためのデータ型で、例えば任意の AD 型を置き換えるために使用されます。
