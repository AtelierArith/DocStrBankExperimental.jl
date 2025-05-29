```julia
System(
    parms::ActinRingsMC.SystemParams,
    filaments::Vector{ActinRingsMC.Filament},
    radius::Float64
) -> ActinRingsMC.System

```

System data, including parameters and positions of filaments.

The given radius should be that corresponding to the lattice height used to create the lattice and the starting configuration of the filaments.
