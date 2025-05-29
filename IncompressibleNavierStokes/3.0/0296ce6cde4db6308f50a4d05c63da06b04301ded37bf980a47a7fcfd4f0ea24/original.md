```julia
struct DirichletBC{U} <: IncompressibleNavierStokes.AbstractBC
```

Dirichlet boundary conditions for the velocity, where `u[1] = (x..., t) -> u1_BC` up to `u[d] = (x..., t) -> ud_BC`, where `d` is the dimension.

When `u` is `nothing`, then the boundary conditions are no slip boundary conditions, where all velocity components are zero.

## Fields

  * `u`: Boundary condition
