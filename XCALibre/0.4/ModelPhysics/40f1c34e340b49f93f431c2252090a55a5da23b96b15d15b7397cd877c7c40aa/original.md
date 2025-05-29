```
Physics(; time, fluid, turbulence, energy, domain)::Physics{T,F,M,Tu,E,D,BI}
```

`Physics` constructor part of the top-level API. It can be used to define the Physics and models relevant to a simulation. This constructor uses keyword arguments to allow users to fine-tune their simulations, whilst some fields are auto-generated behind the scenes for convenience (`Momentum` and `boundary_info`). Where:

  * `time` - specified the time model (Steady or Transient)
  * `fluid` - specifies the type of fluid (Incompressible, etc.)
  * `turbulence` - specified the Turbulence model
  * `energy` - specifies the Energy treatment
  * `domain` - provides the mesh to used (must be adapted to the target backend device)
