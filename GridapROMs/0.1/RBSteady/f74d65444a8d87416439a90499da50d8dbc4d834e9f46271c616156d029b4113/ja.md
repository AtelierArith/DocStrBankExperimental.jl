```
reduced_weak_form(
  solver::RBSolver,
  op::ParamOperator,
  red_trial::RBSpace,
  red_test::RBSpace,
  s::AbstractSnapshots
  ) -> (AffineContribution,Union{AffineContribution,TupOfAffineContribution})
```

`op`に含まれる残差/ヤコビ行列をハイパーリダクションを通じて削減します。詳細については、関数[`reduced_residual`](@ref)および[`reduced_jacobian`](@ref)を確認してください。
