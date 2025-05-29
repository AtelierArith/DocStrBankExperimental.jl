```julia
FullHamiltonian(uc::UnitCell, bz::BZ) --> Matrix{Matrix{ComplexF64}}
```

Returns the full Hamiltonian at all momentum points in `BZ`, corresponding to the bonds present in `UnitCell`.
