```julia
struct DefCont{Tdo, Talg, Tps, Tas, Tud, Tk} <: BifurcationKit.AbstractContinuationAlgorithm
```

Deflated continuationに特有のパラメータを保持する構造体です。

# フィールド

  * `deflation_operator::Any`: デフレーションオペレーター、`::DeflationOperator` デフォルト: nothing
  * `alg::Any`: 予測子として使用される、`::AbstractContinuationAlgorithm`。例えば `PALC()`, `Natural()`,... デフォルト: PALC()
  * `max_branches::Int64`: 計算される最大（アクティブ）ブランチ数 デフォルト: 100
  * `seek_every_step::Int64`: 各ステップで新しい（デフレートされた）解を探すかどうか デフォルト: 1
  * `max_iter_defop::Int64`: デフレートされたニュートン反復の最大数 デフォルト: 5
  * `perturb_solution::Any`: 擾乱関数 デフォルト: _perturbSolution
  * `accept_solution::Any`: 受け入れ（解）関数 デフォルト: _acceptSolution
  * `update_deflation_op::Any`: デフレーションオペレーターを更新する関数、つまり新しい解をプッシュする デフォルト: _updateDeflationOp
  * `jacobian::Any`: デフレートされたニュートンのヤコビ行列。`DeflatedProblemCustomLS()`, または `Val(:autodiff)`, `Val(:fullIterative)` である可能性があります デフォルト: DeflatedProblemCustomLS()
