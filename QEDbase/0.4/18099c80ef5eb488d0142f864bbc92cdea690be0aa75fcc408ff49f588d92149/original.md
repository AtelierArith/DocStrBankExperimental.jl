```
multiplicity(proc::AbstractProcessDefinition)
```

Return the number of spin and polarization combinations represented by `proc` total. This depends on the specific [`AbstractSpinOrPolarization`](@ref)s returned by [`spin_pols`](@ref) for `proc`. For example, a default Compton process with four indefinite spins/polarizations has a multiplicity of 2^4 = 16. A Compton process with many incoming photons that have synced polarizations will still have a multiplicity of 16.

!!! note "Performance"
    As long as [`incoming_spin_pols`](@ref) and [`outgoing_spin_pols`](@ref) can be evaluated at compile time, this function is completely compiled away.


!!! note "Incoming and Outgoing Spins/Polarizations"
    Note that the total multiplicity is not necessarily the incoming and outgoing multiplicities multiplied. This is the case when incoming and outgoing particles are synced with one another.


See also: [`SyncedPolarization`](@ref), [`SyncedSpin`](@ref), [`incoming_multiplicity`](@ref), [`outgoing_multiplicity`](@ref)
