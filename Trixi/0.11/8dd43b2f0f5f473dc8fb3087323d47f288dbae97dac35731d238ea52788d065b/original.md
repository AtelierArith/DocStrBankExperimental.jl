```
struct Adiabatic
```

Used to create a no-slip boundary condition with [`BoundaryConditionNavierStokesWall`](@ref). The field `boundary_value_normal_flux_function` should be a function with signature `boundary_value_normal_flux_function(x, t, equations)` and return a scalar value for the normal heat flux at point `x` and time `t`.
