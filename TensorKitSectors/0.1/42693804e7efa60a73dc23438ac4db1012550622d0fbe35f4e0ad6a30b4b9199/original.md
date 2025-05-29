```
const FermionNumber = U1Irrep ⊠ FermionParity
FermionNumber(a::Int)
```

Represents the fermion number as the direct product of a $U₁$ irrep `a` and a fermion parity, with the restriction that the fermion parity is odd if and only if `a` is odd.

See also: [`U1Irrep`](@ref), [`FermionParity`](@ref)
