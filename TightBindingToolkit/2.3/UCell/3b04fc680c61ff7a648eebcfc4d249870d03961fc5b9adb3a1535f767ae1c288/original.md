```julia
GetRealSpacePositions(uc::UnitCell{T} ; OffsetRange::Int64 = 2) --> Dict
```

Returns a dictionary whose keys are vectors in the cartesian coordinates (rounded off to `accuracy` digits), with values giving the corresponding sublattice and Unit Cell coordinate of a lattice site at that position.
