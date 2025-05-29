```
SimulatorODEForwardSolver{algType,uType,tType,iip,integratorType<:AbstractODEIntegrator{algType,iip,uType,tType}} <: AbstractODEIntegrator{algType,iip,uType,tType}
```

Specialized integrator type that wraps a SciML ODE integrator and controls the stepping procedure such that each observable sample point is hit.
