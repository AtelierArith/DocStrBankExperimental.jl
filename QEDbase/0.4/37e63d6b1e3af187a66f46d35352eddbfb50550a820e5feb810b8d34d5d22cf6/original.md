```
spin_pols(proc_def::AbstractProcessDefinition, dir::ParticleDirection)
```

Return the tuple of spins and polarizations for the process in the given direction. Dispatches to [`incoming_spin_pols`](@ref) or [`outgoing_spin_pols`](@ref).
