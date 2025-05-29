```
incoming_multiplicity(proc::AbstractProcessDefinition)
```

Return the number of spin and polarization combinations represented by `proc`s incoming particles. This function only considers the incoming particles' spins and polarizations, returned by [`incoming_spin_pols`](@ref) for `proc`.

!!! note "Incoming and Outgoing Spins/Polarizations"
    Note that the total multiplicity is not necessarily the incoming and outgoing multiplicities multiplied. For the total process multiplicity, see [`multiplicity`](@ref).


See also: [`SyncedPolarization`](@ref), [`SyncedSpin`](@ref), [`multiplicity`](@ref), [`outgoing_multiplicity`](@ref)
