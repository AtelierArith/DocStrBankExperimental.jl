```
get_solver_result(ams::AbstractManoptSolverState)
get_solver_result(tos::Tuple{AbstractManifoldObjective,AbstractManoptSolverState})
get_solver_result(o::AbstractManifoldObjective, s::AbstractManoptSolverState)
```

すべての反復の後に最終結果を返します。これは、反復中に変更された[`AbstractManoptSolverState`](@ref) `ams`内に保存されています。

目的が渡された場合でも、デフォルトでは目的は無視され、状態のソルバー結果が呼び出されます。
