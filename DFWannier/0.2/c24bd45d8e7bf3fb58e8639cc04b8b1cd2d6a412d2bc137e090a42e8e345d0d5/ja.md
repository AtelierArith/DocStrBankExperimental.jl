```
wannierbands(hamiltonian::TBHamiltonian, kpoints::Vector{Vec3})
wannierbands(hamiltonian::TBHamiltonian, bands::Vector{DFControl.AbstractBand}
```

与えられた*k*-点のセットと[`TBHamiltonian`](@ref TBOperator)に対して全バンド構造を構築します。
