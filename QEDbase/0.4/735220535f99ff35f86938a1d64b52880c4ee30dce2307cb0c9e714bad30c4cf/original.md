```
incoming_particles(proc_def::AbstractProcessDefinition)
```

Interface function for scattering processes. Return a tuple of the incoming particles for the given process definition. This function needs to be given to implement the scattering process interface.

!!! note "Performance"
    It is very beneficial for the performance of derived functions if this function returns compile-time-known values.


See also: [`AbstractParticleType`](@ref)
