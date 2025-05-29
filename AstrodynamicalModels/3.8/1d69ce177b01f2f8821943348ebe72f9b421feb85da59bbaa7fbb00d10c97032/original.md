```julia
mutable struct CartesianSTM{F} <: StaticArraysCore.FieldMatrix{6, 6, F}
```

A mutable matrix, with labels, for a 6DOF Cartesian state transition matrix.
