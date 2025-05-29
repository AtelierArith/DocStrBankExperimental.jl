```
Checkpointer(folder = nothing) <: AbstractCallback
```

An helper class for saving a [`FluxModule`](@ref) and the fit state. The checkpoint is saved as a JLD@ file with the name `ckpt_epoch=X_step=Y.jld2`. A symbolic link to the last checkpoint is also created as `ckpt_last.jld2`.

A `Checkpointer` is automatically created when `checkpointer = true` is passed to [`fit!`](@ref).

If `folder` is not specified, the checkpoints are saved in a folder named `checkpoints` in the run directory.

See also: [`load_checkpoint`](@ref).

# Examples

```julia
checkpointer = Checkpointer()
Tsunami.fit!(..., callbacks = [checkpointer])
```
