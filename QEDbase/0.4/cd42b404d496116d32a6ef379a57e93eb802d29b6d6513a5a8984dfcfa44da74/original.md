```
number_particles(proc_def::AbstractProcessDefinition, dir::ParticleDirection)
```

Convenience function dispatching to [`number_incoming_particles`](@ref) or [`number_outgoing_particles`](@ref) depending on the given direction, returning the number of incoming or outgoing particles, respectively.
