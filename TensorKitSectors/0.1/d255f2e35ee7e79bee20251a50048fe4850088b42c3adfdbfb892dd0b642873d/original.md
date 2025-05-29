```
const FermionSpin = SU2Irrep ⊠ FermionParity
FermionSpin(j::Real)
```

Represents the fermion spin as the direct product of a $SU₂$ irrep `j` and a fermion parity, with the restriction that the fermion parity is odd if `2 * j` is odd.

See also: [`SU2Irrep`](@ref), [`FermionParity`](@ref)
