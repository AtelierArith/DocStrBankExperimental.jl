```
function IncompressibleNavierStokesProblem(
    dimension::Int = 2;
    viscosity = 1.0,
    nonlinear::Bool = false,
    newton::Bool = false,
    nopressureconstraint::Bool = false,
    pmean = 0)
```

Creates a PDEDescription for the incompressible (Navier-)Stokes equations of the specified dimension and globally constant viscosity parameter. If nonlinear = true the nonlinear convection term is added to the PDEDescription. If also newton = true, a Newton iteration is devised for the convection term.
