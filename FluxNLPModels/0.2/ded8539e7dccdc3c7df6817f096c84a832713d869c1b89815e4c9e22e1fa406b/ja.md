```
FluxNLPModel{T, S, C } <: AbstractNLPModel{T, S}
```

データ構造は、[Flux.jl](https://fluxml.ai/) と [NLPModels](https://github.com/JuliaSmoothOptimizers/NLPModels.jl) で定義されたニューラルネットワーク間のインターフェースを作成します。FluxNLPModel には以下のフィールドがあります。

# 引数

  * `meta` と `counters` は `FluxNLPModel` に関する情報を保持します；
  * `chain` はニューラルネットワークを表す連鎖構造です；
  * `data_train` は完全なトレーニングデータセットです；
  * `data_test` は完全なテストデータです；
  * `size_minibatch` はトレーニングおよびテストのミニバッチのサイズをパラメータ化します；
  * `training_minibatch_iterator` はトレーニングミニバッチのイテレータです；
  * `test_minibatch_iterator` はテストミニバッチのイテレータです；
  * `current_training_minibatch` はニューラルネットワークを評価するために使用されるトレーニングミニバッチです；
  * `current_minibatch_test` は現在のテストミニバッチで、実際には使用されません；
  * `w` は重み/変数のベクトルです；
