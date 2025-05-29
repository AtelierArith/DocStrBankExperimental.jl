```
val_step(model, trainer, batch, [batch_idx])
```

The method called at each validation step during `Tsunami.fit!`. Tipically used for computing metrics and statistics on the validation  batch `batch`. The optional argument `batch_idx` is the index of the batch in the current  validation epoch. 

A `Model <: FluxModule` should implement either  `val_step(model::Model, trainer, batch)` or `val_step(model::Model, trainer, batch, batch_idx)`.

Optionally, the method can return a scalar or a named tuple, to be used in hooks such as  [`on_val_batch_end`](@ref).

See also [`train_step`](@ref).

# Examples

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
