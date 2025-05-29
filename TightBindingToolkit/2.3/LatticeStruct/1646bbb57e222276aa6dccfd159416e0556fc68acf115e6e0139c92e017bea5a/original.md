```julia
FillBonds!(lattice::Lattice{T} ; null_dist::Float64 = -1.0, null_label::String = "-" ) where {T}
```

Fills all the bond information in the lattice using the bonds in `UnitCell`.
