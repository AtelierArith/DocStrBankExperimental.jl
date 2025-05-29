```
Incompressible <: AbstractIncompressible
```

Incompressible fluid model containing fluid field parameters for incompressible flows.

### Fields

  * 'nu'   – Fluid kinematic viscosity.
  * 'rho'  – Fluid density.

### Examples

  * `Fluid{Incompressible}(nu=0.001, rho=1.0)` - Constructor with default values.
