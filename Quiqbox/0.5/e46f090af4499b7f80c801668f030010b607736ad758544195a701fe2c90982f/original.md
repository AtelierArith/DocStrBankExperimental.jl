```
MatterByHF{T, D, NN, BN, HFTS} <:MatterData{T, D}
```

Container of the electronic structure information of a quantum system.

≡≡≡ Field(s) ≡≡≡

`Ehf::T`: Hartree–Fock energy of the electronic Hamiltonian.

`nuc::NTuple{NN, String}`: The nuclei in the studied system.

`nucCoord::NTuple{NN, NTuple{D, T}}`: The coordinates of corresponding nuclei.

`Enn::T`: The nuclear repulsion energy.

`Ns::NTuple{HFTS, Int}`: The number(s) of electrons with same spin configurations(s). For  restricted closed-shell Hartree–Fock (RHF), the single element in `.Ns` represents both  spin-up electrons and spin-down electrons.

`occu::NTuple{HFTS, NTuple{BN, Int}}`: Occupations of canonical orbitals.

`occuOrbital::NTuple{HFTS, Tuple{Vararg{CanOrbital{T, D, NN}}}}`: The occupied canonical  orbitals.

`unocOrbital::NTuple{HFTS, Tuple{Vararg{CanOrbital{T, D, NN}}}}` The unoccupied canonical  orbitals.

`occuC::NTuple{HFTS, Matrix{T}}`: Coefficient matrix(s) of occupied canonical orbitals.

`unocC::NTuple{HFTS, Matrix{T}}`: Coefficient matrix(s) of unoccupied canonical orbitals.

`coreHsameSpin::NTuple{HFTS, Matrix{T}}`: Core Hamiltonian(s) (one-body integrals) of the  canonical orbitals with same spin configuration(s).

`eeIsameSpin::NTuple{HFTS, Array{T, 4}}`: electron-electron interactions (two-body  integrals) of the canonical orbitals with same spin configuration(s).

`eeIdiffSpin::Matrix{T}`: Coulomb interactions between canonical orbitals with different  spins.

`basis::GTBasis{T, D, BN}`: The basis set used for the Hartree–Fock approximation.

≡≡≡ Initialization Method(s) ≡≡≡

```
MatterByHF(HFres::HFfinalVars{T, D, <:Any, NN, BN, HFTS}; 
           roundAtol::Real=getAtolVal(T)) where {T, D, NN, BN, HFTS} -> 
MatterByHF{T, D, NN, BN, HFTS}
```

Construct a `MatterByHF` from the result of a Hartree–Fock method `HFres`.  Each parameter stored in the constructed [`CanOrbital`](@ref)s in `.occuOrbital` and  `.unocOrbital` will be rounded to the nearest multiple of `roundAtol`; when `roundAtol` is  set to `NaN`, no rounding will be performed.
