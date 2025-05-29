```julia
struct SymmetricBC <: IncompressibleNavierStokes.AbstractBC
```

Symmetric boundary conditions. The parallel velocity and pressure is the same at each side of the boundary. The normal velocity is zero.

## Fields
