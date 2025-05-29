```
checkpointing(level=1, filename::AbstractString=""; kwargs...)
```

Start a checkpointing actor and return a [`Link`](@ref) to it.

# Arguments

  * `filename::AbstractString`: filename where the actor should save its   checkpointing buffer,
  * `on::Bool=false`: should checkpoints automatically be updated and saved,
  * `update::Int=10`: update interval in seconds ≥ 1,
  * `save::Int=60`: saving interval in seconds ≥ 1,
  * `kwargs...`: keyword arguments to [`spawn`](@ref).

!!! note
    Updating or saving is only done automatically if their intervals are ≥ 1 seconds.

