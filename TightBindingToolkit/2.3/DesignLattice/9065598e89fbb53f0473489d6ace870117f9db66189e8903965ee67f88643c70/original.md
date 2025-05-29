```julia
ModifyLattice!(lattice::Lattice{T}, param::Param{T}) where {T}
ModifyLattice!(lattice::Lattice{T}, params::Vector{Param{T}}) where {T}
```

Modifies a lattice when the `Param` objects given in `params` are modified.
