```
on_train_epoch_end([callback,] model, trainer)
```

各トレーニングエポックの終了時に呼び出されます。

エポックの終了時にすべてのバッチ出力にアクセスするには、モデルの属性としてステップ出力をキャッシュし、このフックでアクセスできます。

[`on_train_epoch_start`](@ref)も参照してください。

# 例

```julia
struct Callback
    training_step_outputs::Vector{Float32}
    # 他のフィールド...
end

function Tsunami.train_step(model::MyModel, trainer, batch)
    ...
    return (loss = loss, accuracy = accuracy)
end

function Tsunami.on_train_epoch_start(cb::Callback, model, trainer)
    empty!(cb.training_step_outputs)
end

function Tsunami.on_train_batch_end(cb::Callback, model, trainer, out, batch, batch_idx)
    push!(cb.training_step_outputs, out.accuracy)
end

function Tsunami.on_train_epoch_end(cb::Callback, model, trainer)
    println("平均精度: ", mean(cb.training_step_outputs))
end
```
