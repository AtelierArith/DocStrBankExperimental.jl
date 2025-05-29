```
solution_snapshots(solver::NonlinearSolver,feop::ParamOperator,r::Realization) -> SteadySnapshots
solution_snapshots(solver::ODESolver,feop::TransientParamOperator,r::TransientRealization,u0) -> TransientSnapshots
```

FE演算子`feop`にエンコードされた問題は何度も解かれ、解のスナップショットとFE法の計算コストに関連する情報が返されます。過渡的な設定では、初期条件`u0`を提供する必要があります。
