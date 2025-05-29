```julia
ScaleLattice!(lattice::Lattice{T}, param::Param{T}) where {T}
ScaleLattice!(lattice::Lattice{T}, params::Vector{Param{T}}) where {T}
```

Scales a lattice bond assuming that the `Param` objects got their strengths modified.
