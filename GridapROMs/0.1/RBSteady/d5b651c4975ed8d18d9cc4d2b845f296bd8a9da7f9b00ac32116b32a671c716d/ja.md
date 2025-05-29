```
reduced_spaces(solver::RBSolver,feop::ParamOperator,s::AbstractSnapshots
  ) -> (RBSpace, RBSpace)
```

テストおよび試行の `FESpace` の部分空間を、スナップショット `s` を圧縮することによって FE 演算子 `feop` に含まれるように計算します。
