```
Tsunami.log(trainer::Trainer, name::AbstractString, value; 
    [on_step, on_epoch, prog_bar, batchsize])
```

Log a `value` with name `name`. Can be called from any function in the training loop or from a callback. Logs to the loggers specified in `trainer.loggers`.

See the [Logging](@ref) docs for more details.

If `on_step` is `true`, the value will be logged on each step. If `on_epoch` is `true`, the value will be accumulated and logged on each epoch. In this case, the default reduction is the `mean` over the batches, which will also take into account the batch size. If both `on_step` and `on_epoch` are `true`, the values will be logged as  `"<name>_step"` and `"<name>_epoch"`

# Arguments

  * `trainer::Trainer`: The trainer object.
  * `name::AbstractString`: The name of the value.
  * `value`: The value to log.
  * `batchsize`: The size of the current batch. Used only when `on_epoch == True`             to compute the aggregate the batches. Defaults to `trainer.fit_state.batchsize`.
  * `on_epoch::Bool`: Whether to log the value on each epoch.                    Defaults to `true` if `stage` is `:train_epoch_end` or `:val_epoch_end`,                    `false` otherwise.
  * `on_step::Bool`: Whether to log the value on each step.                  Defaults to `true` if `stage` is `:training`, `false` for `:validation` and `:testing`.
  * `prog_bar::Bool`: Whether to log the value to the progress bar. Defaults to `true`.

# Examples

```julia
function val_step(model::Model, trainer, batch, batch_idx)
    # log the validation loss
    ...
    Tsunami.log(trainer, "val/loss", val_loss)
end
```
