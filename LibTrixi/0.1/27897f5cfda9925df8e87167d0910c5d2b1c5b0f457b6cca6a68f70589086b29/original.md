```
trixi_initialize_simulation(libelixir::Cstring)::Cint
trixi_initialize_simulation(libelixir::AbstractString)::Cint
```

Initialize a new simulation based on the file `libelixir`and return a handle to the corresponding [`SimulationState`](@ref) as a `Cint` (i.e, a plain C `int`).

The libelixir has a similar purpose as a regular "elixir" in Trixi.jl, as it completely defines a simulation setup in Julia code. A key difference (and thus the name libelixir) is that instead of running a simulation directly, it should define an argument-less function named `init_simstate()` that returns a [`SimulationState`](@ref) with the complete simulation setup. `trixi_initialize_simulation` will store the `SimulationState` object internally and allow one to use it in subsequent calls to libtrixi via the handle returned from this function.

For convenience, when using LibTrixi.jl directly from Julia, one can also pass a regular `String` in the `libelixir` argument.

!!! note "Libelixir hygiene and `init_simstate`"
    The libelixir file will be evaluated in the `Main` module. Thus any previously defined function `init_simstate` will be overwritten, and any variables defined outside the function will live throughout the lifetime of the Julia process.


!!! warning "Thread safety"
    **This function is not thread safe.** Since the libelixir file will be evaluated in the `Main` module, calling `trixi_initialize_simulation` simultaneously from different threads can lead to undefined behavior.

