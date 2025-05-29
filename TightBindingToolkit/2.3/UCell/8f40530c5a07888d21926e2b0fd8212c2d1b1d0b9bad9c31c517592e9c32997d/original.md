```julia
IsSameUnitCell(uc_1::UnitCell, uc_2::UnitCell) --> Bool
```

Function to check if two unit cell live on the same underlying lattice or not, i.e. have the same `primitives`, same `sublattices`, and same `localDim`.
