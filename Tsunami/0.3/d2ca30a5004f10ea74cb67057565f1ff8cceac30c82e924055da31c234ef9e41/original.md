```
train_step(model, trainer, batch, [batch_idx])
```

The method called at each training step during `Tsunami.fit!`. It should compute the forward pass of the model and return the loss  (a scalar) corresponding to the minibatch `batch`.  The optional argument `batch_idx` is the index of the batch in the current epoch.

Any `Model <: FluxModule` should implement either  `train_step(model::Model, trainer, batch)` or `train_step(model::Model, trainer, batch, batch_idx)`.

The training loop in `Tsunami.fit!` approximately looks like this:

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

The output can be either a scalar or a named tuple:

  * If a scalar is returned, it is assumed to be the loss.
  * If a named tuple is returned, it has to contain the `loss` field.

The output can be accessed in hooks such as [`on_before_update`](@ref) or [`on_train_batch_end`](@ref).

# Examples

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
