```
simulate!(sim::JutulSimulator, timesteps::AbstractVector;
    forces = nothing,
    config = nothing,
    initialize = true,
    restart = nothing,
    state0 = nothing,
    parameters = nothing,
    kwarg...
)
```

Non-allocating (or perhaps less allocating) version of [`simulate!`](@ref).

# Arguments

  * `initialize=true`: Perform internal updates as if this is the first time

See also [`simulate`](@ref) for additional supported input arguments.
