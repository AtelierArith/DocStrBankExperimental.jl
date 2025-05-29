```julia
mutable struct CartesianState{F} <: AstrodynamicalModels.AstrodynamicalState{F, 6}
```

A mutable vector, with labels, for 6DOF Cartesian states.
