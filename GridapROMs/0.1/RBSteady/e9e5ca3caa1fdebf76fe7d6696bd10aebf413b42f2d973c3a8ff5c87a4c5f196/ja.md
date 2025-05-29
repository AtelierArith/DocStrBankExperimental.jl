```
residual_snapshots(solver::RBSolver,op::ParamOperator,s::AbstractSnapshots;nparams) -> Contribution
residual_snapshots(solver::RBSolver,op::ODEParamOperator,s::AbstractSnapshots;nparams) -> Contribution
```

FE演算子`op`に対する残差`Contribution`を返します。量`s`は、残差を評価する解のスナップショットを示します。`s`を計算するために使用されるパラメータの数に比べて、より少ない数のパラメータ`nparams`を選択できることに注意してください。
