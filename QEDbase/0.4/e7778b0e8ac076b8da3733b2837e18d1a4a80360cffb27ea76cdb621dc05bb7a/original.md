```
incoming_spin_pols(proc_def::AbstractProcessDefinition)
```

Interface function for scattering processes. Return the tuple of spins or polarizations for the given process definition. The order must be the same as the particles returned from [`incoming_particles`](@ref). A default implementation is provided, returning [`AllSpin`](@ref) for every [`is_fermion`](@ref) and [`AllPolarization`](@ref) for every [`is_boson`](@ref).

!!! note "Performance"
    It is very beneficial for the performance of derived functions if this function returns compile-time-known values.


See also: [`AbstractSpinOrPolarization`](@ref)
