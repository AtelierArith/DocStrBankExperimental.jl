```
load_checkpoint(path)
```

`path`に保存されたチェックポイントを読み込みます。モデルの状態、フィット状態、lrスケジューラ、およびオプティマイザを含むnamedtupleを返します。

関連情報: [`Checkpointer`](@ref)。

# 例

```julia
ckpt = load_checkpoint("checkpoints/ckpt_last.jld2")
model = MyModel(...)
Flux.loadmodel!(model, ckpt.model_state)
```
