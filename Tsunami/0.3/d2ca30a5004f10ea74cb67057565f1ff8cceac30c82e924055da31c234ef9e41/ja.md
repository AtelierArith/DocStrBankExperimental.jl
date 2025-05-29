```
train_step(model, trainer, batch, [batch_idx])
```

`Tsunami.fit!`の各トレーニングステップで呼び出されるメソッドです。モデルのフォワードパスを計算し、ミニバッチ`batch`に対応する損失（スカラー）を返す必要があります。オプションの引数`batch_idx`は、現在のエポックにおけるバッチのインデックスです。

`Model <: FluxModule`の任意のモデルは、`train_step(model::Model, trainer, batch)`または`train_step(model::Model, trainer, batch, batch_idx)`のいずれかを実装する必要があります。

`Tsunami.fit!`のトレーニングループはおおよそ次のようになります：

```julia
for epoch in 1:epochs
    for (batch_idx, batch) in enumerate(train_dataloader)
        grads = gradient(model) do m
            loss = train_step(m, trainer, batch, batch_idx)
            return loss
        end
        Optimisers.update!(opt, model, grads[1])
    end
end
```

出力はスカラーまたは名前付きタプルのいずれかです：

  * スカラーが返される場合、それは損失であると見なされます。
  * 名前付きタプルが返される場合、`loss`フィールドを含む必要があります。

出力は、[`on_before_update`](@ref)や[`on_train_batch_end`](@ref)などのフックでアクセスできます。

# 例

```julia
function Tsunami.train_step(model::Model, trainer, batch)
    x, y = batch
    ŷ = model(x)
    loss = Flux.Losses.logitcrossentropy(ŷ, y)
    Tsunami.log(trainer, "loss/train", loss)
    Tsunami.log(trainer, "accuracy/train", Tsunami.accuracy(ŷ, y))
    return loss
end
```
