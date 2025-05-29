```
struct Isothermal
```

Used to create a no-slip boundary condition with [`BoundaryConditionNavierStokesWall`](@ref). The field `boundary_value_function` should be a function with signature `boundary_value_function(x, t, equations)` and return a scalar value for the temperature at point `x` and time `t`.
