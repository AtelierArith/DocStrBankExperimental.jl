```
GTBasis{T, D, BN, BFT<:GTBasisFuncs{T, D, 1}} <: BasisSetData{T, D, BFT}
```

The container of basis set information.

≡≡≡ Field(s) ≡≡≡

`basis::Vector{BFT}`: Stored basis set with its size equal to `BN` by default  (assuming no deleting or appending to basis set has been made).

`S::Matrix{T}`: Overlap matrix.

`Te::Matrix{T}`: Kinetic energy part of the electronic core Hamiltonian.

`eeI::Array{T, 4}`: Electron-electron interaction.

≡≡≡ Initialization Method(s) ≡≡≡

```
GTBasis(basis::Union{Tuple{Vararg{GTBasisFuncs{T, D}}}, 
                     AbstractVector{<:GTBasisFuncs{T, D}}}) where {T, D} -> 
GTBasis{T, D}
```

Construct a `GTBasis` given a basis set.
