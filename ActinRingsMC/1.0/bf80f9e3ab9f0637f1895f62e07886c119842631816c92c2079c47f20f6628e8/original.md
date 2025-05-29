```julia
generate_starting_config(
    lattice::ActinRingsMC.Lattice,
    Nfil::Int64,
    Nsca::Int64,
    lf::Int64,
    overlap::Int64
) -> Vector{ActinRingsMC.Filament}

```

Generate a starting configuration with uniform overlaps.

The number of scaffold filament Nsca and the number of lattices lf must be even.
