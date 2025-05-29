```julia
struct PressureBC <: IncompressibleNavierStokes.AbstractBC
```

Pressure boundary conditions. The pressure is prescribed on the boundary (usually an "outlet"). The velocity has zero Neumann conditions.

Note: Currently, the pressure is prescribed with the constant value of zero on the entire boundary.

## Fields
