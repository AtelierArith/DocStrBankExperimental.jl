```
BoundaryConditionNeumann(boundary_normal_flux_function)
```

Similar to `BoundaryConditionDirichlet`, but creates a Neumann boundary condition for parabolic equations that uses the function `boundary_normal_flux_function` to specify the values of the normal flux at the boundary. The passed boundary value function will be called with the same arguments as an initial condition function is called, i.e., as

```julia
boundary_normal_flux_function(x, t, equations)
```

where `x` specifies the coordinates, `t` is the current time, and `equation` is the corresponding system of equations.
