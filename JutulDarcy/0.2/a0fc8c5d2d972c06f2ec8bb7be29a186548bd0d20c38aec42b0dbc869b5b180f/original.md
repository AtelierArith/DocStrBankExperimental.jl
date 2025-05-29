```
flow_boundary_condition(cells, domain, pressures, temperatures = 298.15; kwarg...)
```

Add flow boundary conditions to a vector of `cells` for a given `domain` coming from `reservoir_domain`. The input arguments `pressures` and `temperatures` can either be scalars or one value per cell. Other keyword arguments are passed onto the `FlowBoundaryCondition` constructor.

The output of this function is a `Vector` of boundary conditions that can be passed on the form `forces = setup_reservoir_forces(model, bc = bc)`.
