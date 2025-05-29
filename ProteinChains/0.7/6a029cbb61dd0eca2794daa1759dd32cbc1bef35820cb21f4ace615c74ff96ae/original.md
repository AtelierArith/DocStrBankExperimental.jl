```
ProteinStructure{T} <: AbstractVector{ProteinChain{T}}
```

## Fields

  * `name::String`: Usually just the base name of the original file.
  * `chains::Vector{ProteinChain{T}}`: a collection of `ProteinChain`s.
  * `atoms::Vector{Atom{T}}`: free atoms from the structure that were not part of any protein residue.
