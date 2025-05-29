addparticle!(sim::Simulation{*, PT}; params, _parent*id = UInt64(0), kwargs...) → id::UInt64 Create a new particle of type `PT` with fixed parameters `params` and add it to the simulation `sim`. `_parent_id` is used to obtain a new ID from the registrar, all other keyword arguments are passed on to the `kwarg`-only constructor of `PT`.

Returns the particle id.

# Extended help

New particles are added to a temporary buffer, which is automatically flushed by [`evolve!`](@ref) on initialization and after every time step. To manually flush the buffer, use [`flushadditions!(sim)`](@ref).

!!! warning
    Flushing the buffer manually while running a simulation is not recommended and may cause the simulation to enter an invalid state!

