```
reduced_jacobian(
  solver::RBSolver,
  op::ParamOperator,
  red_trial::RBSpace,
  red_test::RBSpace,
  s::AbstractSnapshots
  ) -> Union{AffineContribution,TupOfAffineContribution}
```

`op` に含まれるヤコビ行列をハイパーリダクションを通じて削減します。この関数はまずヤコビ行列のスナップショットを構築し、それをリダクションソルバー `solver` で指定された戦略 `reduced_jacobian` に従って削減します。過渡的なアプリケーションでは、出力はヤコビ行列の数（すなわち、ODEの次数に1を加えたもの）に等しい長さのタプルです。
