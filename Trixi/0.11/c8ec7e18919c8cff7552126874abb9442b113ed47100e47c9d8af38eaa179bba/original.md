```
BoundaryConditionDirichlet(boundary_value_function)
```

Create a Dirichlet boundary condition that uses the function `boundary_value_function` to specify the values at the boundary. This can be used to create a boundary condition that specifies exact boundary values by passing the exact solution of the equation. The passed boundary value function will be called with the same arguments as an initial condition function is called, i.e., as

```julia
boundary_value_function(x, t, equations)
```

where `x` specifies the coordinates, `t` is the current time, and `equation` is the corresponding system of equations.

# Examples

```julia
julia> BoundaryConditionDirichlet(initial_condition_convergence_test)
```
