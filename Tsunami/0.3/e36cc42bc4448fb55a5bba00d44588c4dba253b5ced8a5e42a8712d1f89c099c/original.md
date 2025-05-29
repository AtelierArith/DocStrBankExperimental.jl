```
load_checkpoint(path)
```

Loads a checkpoint that was saved to `path`.  Returns a namedtuple containing the model state, the fit state, the lr schedulers and the optimisers.

See also: [`Checkpointer`](@ref).

# Examples

```julia
ckpt = load_checkpoint("checkpoints/ckpt_last.jld2")
model = MyModel(...)
Flux.loadmodel!(model, ckpt.model_state)
```
