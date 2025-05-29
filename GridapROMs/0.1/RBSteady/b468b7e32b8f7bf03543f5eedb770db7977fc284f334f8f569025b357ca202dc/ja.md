```
jacobian_snapshots(solver::RBSolver,op::ParamOperator,s::AbstractSnapshots;nparams) -> Contribution
jacobian_snapshots(solver::RBSolver,op::ODEParamOperator,s::AbstractSnapshots;nparams) -> Tuple{Vararg{Contribution}}

FE演算子`op`に関連するヤコビアン`Contribution`を返します。量`s`は、ヤコビアンを評価する解のスナップショットを示します。`s`を計算するために使用されるパラメータの数に比べて、より少ない数のパラメータ`nparams`を選択できることに注意してください。過渡的な設定では、出力はタプルであり、その`n`番目の要素は`n`番目の時間微分に関連するヤコビアンです。
```
