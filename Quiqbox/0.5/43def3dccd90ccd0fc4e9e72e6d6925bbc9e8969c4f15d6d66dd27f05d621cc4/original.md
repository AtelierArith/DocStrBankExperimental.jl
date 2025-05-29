```
CanOrbital{T, D, NN} <: AbstractSpinOrbital{T, D}
```

The spatial part (orbital) of a canonical spin-orbital (the set of which diagonalizes the  Fock matrix of a Hartree–Fock state) with its occupation information. This means the  maximal occupation number for the mode corresponding to the orbital (namely a canonical  orbital) equals 2. Please refer to [`genCanOrbitals`](@ref) for the construction of a  `CanOrbital`.

≡≡≡ Field(s) ≡≡≡

`energy::T`: The eigen energy corresponding to the orbital.

`index::Int`: The index of the orbital within the same spin configuration.

`nuc::NTuple{NN, String}`: The nuclei in the studied system.

`nucCoords::NTuple{NN, NTuple{D, T}}`: The coordinates of corresponding nuclei.

`occu::NTuple{2, Array{Bool, 0}}`: The occupations of two spin configurations.

`orbital::GTBasisFuncs{T, D, 1}`: The spatial orbital part.
