```
process!([clk], prc, cycles; <keyword arguments>)
```

Register a [`Prc`](@ref) to a clock, start an asynchronous task  executing the process function in a loop and return the `id` it  was registered with. It can then be found under `clk.processes[id]`.

# Arguments

  * `c<:AbstractClock`: if not provided, the process runs under `𝐶`,
  * `prc::Prc`: it contains a function and its arguments,
  * `cycles<:Number=Inf`: number of loop cycles the process should run,

# Keyword arguments

  * `cid::Int=clk.id`: if cid ≠ clk.id, assign the event to the parallel clock   with id == cid. This overrides `spawn`,
  * `spawn::Bool=false`: if true, the process may be scheduled on another thread   in parallel and registered to the thread specific clock.
