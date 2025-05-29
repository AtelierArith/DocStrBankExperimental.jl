```
mutable struct Hyperparameters{F <: AbstractFloat, I <: Int} <: AbstractParameters
```

機械学習モデルのトレーニングのためのハイパーパラメータを保持する可変構造体です。

# キーワード引数

  * `current_epoch::I`: 現在のエポック番号。
  * `current_minibatch::I`: 現在のミニバッチ番号。
  * `loss_history::Vector{F}`: 損失値の履歴を格納するベクター。
  * `optimizer::Union{Optim.FirstOrderOptimizer, Flux.Optimise.AbstractOptimiser, Optimisers.AbstractRule}`: トレーニングに使用されるオプティマイザ。
  * `loss_epoch::F`: 現在のエポックの損失値。
  * `epochs::I`: トレーニングのためのエポックの総数。
  * `batch_size::I`: 各ミニバッチのサイズ。
