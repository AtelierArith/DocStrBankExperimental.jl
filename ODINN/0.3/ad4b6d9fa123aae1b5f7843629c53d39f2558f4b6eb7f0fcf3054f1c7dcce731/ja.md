```
ハイパーパラメータ(; current_epoch::Int64 = 1, current_minibatch::Int64 = 1, loss_history::Vector{Float64} = Vector{Float64}(), optimizer::Union{Optim.FirstOrderOptimizer, Flux.Optimise.AbstractOptimiser, Optimisers.AbstractRule} = BFGS(initial_stepnorm=0.001), loss_epoch::Float64 = 0.0, epochs::Int64 = 50, batch_size::Int64 = 15)
```

指定されたパラメータで `Hyperparameters` オブジェクトを構築します。

# 引数

  * `current_epoch::Int64`: 現在のエポック番号。デフォルトは1です。
  * `current_minibatch::Int64`: 現在のミニバッチ番号。デフォルトは1です。
  * `loss_history::Vector{Float64}`: 損失値の履歴を保存するためのベクター。デフォルトは空のベクターです。
  * `optimizer::Union{Optim.FirstOrderOptimizer, Flux.Optimise.AbstractOptimiser, Optimisers.AbstractRule}`: 使用するオプティマイザ。デフォルトは `BFGS(initial_stepnorm=0.001)` です。
  * `loss_epoch::Float64`: 現在のエポックの損失値。デフォルトは0.0です。
  * `epochs::Int64`: 総エポック数。デフォルトは50です。
  * `batch_size::Int64`: 各ミニバッチのサイズ。デフォルトは15です。

# 戻り値

  * 提供された値で初期化された `Hyperparameters` オブジェクト。
