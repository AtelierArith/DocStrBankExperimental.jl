```julia
ExpandUnitCell(ucOG::UnitCell{T}, scaling::Vector{Int64} ; OffsetRange::Int64 = 2)
```

Returns a UnitCell which is an integer multiple of the given UnitCell (the primitives are scaled by the given scalings along each direction). The bonds are properly redefined amongst the new sublattices and new primitive vectors.
