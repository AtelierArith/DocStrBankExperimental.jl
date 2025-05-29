```
struct BoundaryConditionNavierStokesWall
```

Creates a wall-type boundary conditions for the compressible Navier-Stokes equations, see [`CompressibleNavierStokesDiffusion1D`](@ref), [`CompressibleNavierStokesDiffusion2D`](@ref), and [`CompressibleNavierStokesDiffusion3D`](@ref). The fields `boundary_condition_velocity` and `boundary_condition_heat_flux` are intended to be boundary condition types such as the [`NoSlip`](@ref) velocity boundary condition and the [`Adiabatic`](@ref) or [`Isothermal`](@ref) heat boundary condition.
