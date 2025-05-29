```
pressure_force(patch::Symbol, p::ScalarField, rho)
```

Function to calculate the pressure force acting on a given patch/boundary.

# Input arguments

  * `patch::Symbol` name of the boundary of interest (as a `Symbol`)
  * `p::ScalarField` pressure field
  * `rho` density. Set to 1 for incompressible solvers
