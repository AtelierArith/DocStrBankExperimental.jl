```
wannierbands(hamiltonian::TBHamiltonian, kpoints::Vector{Vec3})
wannierbands(hamiltonian::TBHamiltonian, bands::Vector{DFControl.AbstractBand}
```

Constructs the whole bandstructure for a given set of *k*-points and [`TBHamiltonian`](@ref TBOperator).
