```
fit!(model, trainer, train_dataloader, [val_dataloader]; [ckpt_path])
```

Train `model` using the configuration given by `trainer`. If `ckpt_path` is given, training is resumed from the checkpoint.

After the fit, `trainer.fit_state` will contain the final state of the training.

See also [`Trainer`](@ref) and [`FitState`](@ref).

# Arguments

  * **model**: A Flux model subtyping [`FluxModule`](@ref).
  * **trainer**: A [`Trainer`](@ref) object storing the configuration options for `fit!`.
  * **train_dataloader**: An iterator over the training dataset, typically a `Flux.DataLoader`.
  * **val_dataloader**: An iterator over the validation dataset, typically a `Flux.DataLoader`. Default: `nothing`.
  * **ckpt_path**: Path of the checkpoint from which training is resumed. Default: `nothing`.

# Examples

```julia
model = ...
trainer = Trainer(max_epochs = 10)
Tsunami.fit!(model, trainer, train_dataloader, val_dataloader)
run_dir = trainer.fit_state.run_dir

# Resume training from checkpoint
trainer = Trainer(max_epochs = 20) # train for 10 more epochs
ckpt_path = joinpath(run_dir, "checkpoints", "ckpt_last.jld2")
fit_state′ = Tsunami.fit!(model, trainer, train_dataloader, val_dataloader; ckpt_path)
```
