```
WeaklyCompressible <: AbstractCompressible
```

Weakly compressible fluid model containing fluid field parameters for weakly compressible      flows with constant parameters - ideal gas with constant viscosity.

### Fields

  * 'nu'   – Fluid kinematic viscosity.
  * 'cp'   – Fluid specific heat capacity.
  * `gamma` – Ratio of specific heats.
  * `Pr`   – Fluid Prandtl number.

### Examples

  * `Fluid{WeaklyCompressible}(; nu=1E-5, cp=1005.0, gamma=1.4, Pr=0.7)` - Constructor with

default values.
