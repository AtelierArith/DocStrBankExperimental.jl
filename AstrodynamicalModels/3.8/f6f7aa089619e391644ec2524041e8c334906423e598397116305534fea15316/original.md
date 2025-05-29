```julia
mutable struct AttitudeState{F} <: AstrodynamicalModels.AstrodynamicalState{F, 7}
```

A mutable state vector for attitude dynamics.
