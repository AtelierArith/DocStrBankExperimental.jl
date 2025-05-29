```
on_train_epoch_end([callback,] model, trainer)
```

Called at the end of each training epoch.

To access all batch outputs at the end of the epoch,  you can cache step outputs as an attribute of the model and access them in this hook:

See also [`on_train_epoch_start`](@ref).

# Examples

```julia
struct Callback
    training_step_outputs::Vector{Float32}
    # other fields...
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
    println("Mean accuracy: ", mean(cb.training_step_outputs))
end
```
