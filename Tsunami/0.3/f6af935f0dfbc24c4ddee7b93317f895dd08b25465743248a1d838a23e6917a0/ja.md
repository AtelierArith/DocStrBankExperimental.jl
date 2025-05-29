```
abstract type FluxModule end
```

Fluxモデルのための抽象型です。`FluxModule`はコードの整理を助け、トレーニングのための標準インターフェースを提供します。

`FluxModule`は、`Flux.@layer`によって提供される機能（整形表示など）と、[`Trainer`](@ref)および`Optimisers.jl`との相互作用の能力を備えています。

`Optimisers.trainables`を実装することで、トレーニング可能な要素を変更できます。

`FluxModule`からサブタイプ化された型は、[`Trainer`](@ref)と相互作用するために、以下のメソッドを実装する必要があります。

# 必要なメソッド

  * [`configure_optimisers`](@ref)`(model, trainer)`.
  * [`train_step`](@ref)`(model, trainer, batch, [batch_idx])`.

# オプションメソッド

  * [`val_step`](@ref)`(model, trainer, batch, [batch_idx])`.
  * [`test_step`](@ref)`(model, trainer, batch, [batch_idx])`.
  * 一般的な[hooks](@ref Hooks).

# 例

```julia
using Flux, Tsunami, Optimisers

# FluxModuleインターフェースを実装する多層パーセプトロンを定義

struct Model <: FluxModule
    net
end

function Model()
    net = Chain(Dense(4 => 32, relu), Dense(32 => 2))
    return Model(net)
end

(model::Model)(x) = model.net(x)

function Tsunami.train_step(model::Model, trainer, batch)
    x, y = batch
    y_hat = model(x)
    loss = Flux.Losses.mse(y_hat, y)
    return loss
end

function Tsunami.configure_optimisers(model::Model, trainer)
    return Optimisers.setup(Optimisers.Adam(1f-3), model)
end

# データセットとDataLoaderを準備
X, Y = rand(4, 100), rand(2, 100)
train_dataloader = Flux.DataLoader((X, Y), batchsize=10)

# モデルを作成してトレーニング
model = Model()
trainer = Trainer(max_epochs=10)
Tsunami.fit!(model, trainer, train_dataloader)
```
