```julia
struct Orbit{U<:(AbstractVector), P<:(AbstractVector)} <: AstrodynamicalModels.AstrodynamicalOrbit{U<:(AbstractVector), P<:(AbstractVector)}
```

A full representation of an orbit, including a numerical state, and the parameters of the system.
