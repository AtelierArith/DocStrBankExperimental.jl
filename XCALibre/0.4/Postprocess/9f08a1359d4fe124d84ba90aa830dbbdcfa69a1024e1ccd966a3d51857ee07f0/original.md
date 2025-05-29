```
viscous_force(patch::Symbol, U::VectorField, rho, ν, νt)
```

Function to calculate the pressure force acting on a given patch/boundary.

# Input arguments

  * `patch::Symbol` name of the boundary of interest (as a `Symbol`)
  * `U::VectorField` pressure field
  * `rho` density. Set to 1 for incompressible solvers
  * `ν` laminar viscosity of the fluid
  * `νt` eddy viscosity from turbulence models. Pass ConstantScalar(0) for laminar flows
