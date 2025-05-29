```
all_spin_pols(process::AbstractProcessDefinition)
```

This function returns an iterator, yielding every fully definite combination of spins and polarizations allowed by the process' [`spin_pols`](@ref). Each returned element is a Tuple of the incoming and the outgoing spins and polarizations, in the order of the process' own spins and polarizations.

This works together with the definite spins and polarizations, [`AllSpin`](@ref), [`AllPolarization`](@ref), and the synced versions [`SyncedPolarization`](@ref) and [`SyncedSpin`](@ref).

```julia
julia> using QEDbase; using QEDcore; using QEDprocesses;

julia> proc = ScatteringProcess((Photon(), Photon(), Photon(), Electron()), (Photon(), Electron()), (SyncedPolarization(1), SyncedPolarization(2), SyncedPolarization(1), SpinUp()), (SyncedPolarization(2), AllSpin()))
generic QED process
    incoming: photon (synced polarization 1), photon (synced polarization 2), photon (synced polarization 1), electron (spin up)
    outgoing: photon (synced polarization 2), electron (all spins)


julia> for sp_combo in spin_pols_iter(proc) println(sp_combo) end
((x-polarized, x-polarized, x-polarized, spin up), (x-polarized, spin up))
((y-polarized, x-polarized, y-polarized, spin up), (x-polarized, spin up))
((x-polarized, y-polarized, x-polarized, spin up), (y-polarized, spin up))
((y-polarized, y-polarized, y-polarized, spin up), (y-polarized, spin up))
((x-polarized, x-polarized, x-polarized, spin up), (x-polarized, spin down))
((y-polarized, x-polarized, y-polarized, spin up), (x-polarized, spin down))
((x-polarized, y-polarized, x-polarized, spin up), (y-polarized, spin down))
((y-polarized, y-polarized, y-polarized, spin up), (y-polarized, spin down))

julia> length(spin_pols_iter(proc))
8
```
