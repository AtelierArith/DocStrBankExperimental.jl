```
fit!(model, trainer, train_dataloader, [val_dataloader]; [ckpt_path])
```

`model`を`trainer`によって与えられた設定を使用してトレーニングします。`ckpt_path`が指定されている場合、トレーニングはチェックポイントから再開されます。

フィット後、`trainer.fit_state`にはトレーニングの最終状態が含まれます。

[`Trainer`](@ref)および[`FitState`](@ref)も参照してください。

# 引数

  * **model**: [`FluxModule`](@ref)をサブタイプ化したFluxモデル。
  * **trainer**: `fit!`の設定オプションを格納する[`Trainer`](@ref)オブジェクト。
  * **train_dataloader**: トレーニングデータセットに対するイテレータ、通常は`Flux.DataLoader`。
  * **val_dataloader**: 検証データセットに対するイテレータ、通常は`Flux.DataLoader`。デフォルト: `nothing`。
  * **ckpt_path**: トレーニングが再開されるチェックポイントのパス。デフォルト: `nothing`。

# 例

```julia
model = ...
trainer = Trainer(max_epochs = 10)
Tsunami.fit!(model, trainer, train_dataloader, val_dataloader)
run_dir = trainer.fit_state.run_dir

# チェックポイントからトレーニングを再開
trainer = Trainer(max_epochs = 20) # さらに10エポックトレーニング
ckpt_path = joinpath(run_dir, "checkpoints", "ckpt_last.jld2")
fit_state′ = Tsunami.fit!(model, trainer, train_dataloader, val_dataloader; ckpt_path)
```
