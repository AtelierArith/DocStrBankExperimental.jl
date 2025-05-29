```
SimulationModel(g::JutulMesh, system; discretization = nothing, kwarg...)
```

Type that defines a simulation model - everything needed to solve the discrete equations.

The minimal setup requires a [`JutulMesh`](@ref) that defines topology together with a [`JutulSystem`](@ref) that imposes physical laws.
