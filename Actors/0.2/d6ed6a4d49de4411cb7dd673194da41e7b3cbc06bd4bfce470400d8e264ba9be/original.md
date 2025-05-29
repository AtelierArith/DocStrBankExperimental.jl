```
checkpoint(cp::Link, key::Symbol, args...)
```

Tell a checkpointing actor to take a checkpoint.

# Arguments

  * `cp::Link`: [`Link`](@ref) to the checkpointing actor,
  * `key::Symbol`: key for the checkpoint,
  * `args...`: variables to save in the checkpoint,
  * `level::Int=1`: checkpoint level.
