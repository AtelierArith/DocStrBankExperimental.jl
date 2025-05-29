```
Optimizer(method, cache, step, retraction)
```

`method`（例：[`AdamOptimizer`](@ref) と対応するハイパーパラメータ）、`cache`（例：[`AdamCache`](@ref)）、最適化ステップ、およびリトラクションを格納します。

最適化手法とネットワークのパラメータを入力として受け取ります。

`Optimizer`を呼び出す前に、すべてのハイパーパラメータを格納する[`OptimizerMethod`](@ref)を指定する必要があります。

# Functor

`Optimizer`のインスタンス`o`に対して、対応するファンクタを次のように呼び出すことができます：

```julia
o(nn, dl, batch, n_epochs, loss)
```

引数は次のとおりです：

1. `nn::NeuralNetwork`
2. `dl::`[`DataLoader`](@ref)
3. `batch::`[`Batch`](@ref)
4. `n_epochs::Integer`
5. `loss::NetworkLoss`

最後の引数は多くのニューラルネットワークアーキテクチャにとってオプションです。以下のデフォルトがあります：

  * [`TransformerIntegrator`](@ref) は[`TransformerLoss`](@ref)を使用します。
  * [`NeuralNetworkIntegrator`](@ref) は[`FeedForwardLoss`](@ref)を使用します。
  * [`AutoEncoder`](@ref) は[`AutoEncoderLoss`](@ref)を使用します。

さらに、ファンクタに供給できるオプションのキーワード引数があります：

  * `show_progress=true`：これは、トレーニング中に進行状況バーを表示するかどうかを指定します。

# 実装

内部的に`Optimizer`のファンクタは、最初に[`GlobalSection`](@ref)を1回呼び出し、その後各エポックに対して[`optimize_for_one_epoch!`](@ref)を呼び出します。
