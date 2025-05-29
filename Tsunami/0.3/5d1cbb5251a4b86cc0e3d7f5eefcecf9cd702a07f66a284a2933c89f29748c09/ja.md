```
val_step(model, trainer, batch, [batch_idx])
```

`Tsunami.fit!`の各検証ステップで呼び出されるメソッド。通常、検証バッチ`batch`のメトリクスや統計を計算するために使用されます。オプションの引数`batch_idx`は、現在の検証エポックにおけるバッチのインデックスです。

`Model <: FluxModule`は、`val_step(model::Model, trainer, batch)`または`val_step(model::Model, trainer, batch, batch_idx)`のいずれかを実装する必要があります。

オプションで、このメソッドはスカラーまたは名前付きタプルを返すことができ、[`on_val_batch_end`](@ref)のようなフックで使用されます。

また、[`train_step`](@ref)も参照してください。

# 例

```julia
function Tsunami.val_step(model::Model, trainer, batch)
    x, y = batch
    ŷ = model(x)
    loss = Flux.Losses.logitcrossentropy(ŷ, y)
    accuracy = Tsunami.accuracy(ŷ, y)
    Tsunami.log(trainer, "loss/val", loss, on_step = false, on_epoch = true)
    Tsunami.log(trainer, "loss/accuracy", accuracy, on_step = false, on_epoch = true)
end
```
