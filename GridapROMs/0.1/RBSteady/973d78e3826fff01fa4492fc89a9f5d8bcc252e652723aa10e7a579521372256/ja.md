```
reduced_residual(
  solver::RBSolver,
  op::ParamOperator,
  red_test::RBSpace,
  s::AbstractSnapshots
  ) -> AffineContribution
```

`op`に含まれる残差をハイパーリダクションを通じて削減します。この関数はまず残差スナップショットを構築し、それらはリダクスソルバー`solver`で指定された戦略`residual_reduction`に従って削減されます。
