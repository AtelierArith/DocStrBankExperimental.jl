Parameter state for ChabocheThermal material.

The classical viscoplastic material is a special case of this model with `C1 = C2 = C3 = 0`.

Maximum hardening for each backstress is `Cj / Dj`.

Any parameter that is a `Function` should takes a single argument, the absolute temperature.

  * `theta0`: reference temperature at which thermal expansion is considered zero
  * `E`: Young's modulus [N/mm^2]
  * `nu`: Poisson's ratio
  * `alpha`: linear thermal expansion coefficient
  * `R0`: initial yield strength
  * `tvp`: viscoplastic pseudo-relaxation-time (has the units of time)
  * `Kn`: drag stress (has the units of stress)
  * `nn`: Norton-Bailey power law exponent
  * `C1`, `D1`: parameters governing behavior of backstress X1. C1 has the units of stress; D1 is dimensionless.
  * `C2`, `D2`: parameters governing behavior of backstress X2.
  * `C3`, `D3`: parameters governing behavior of backstress X3.
  * `Q`: isotropic hardening saturation state (has the units of stress)
  * `b`: rate of convergence to isotropic hardening saturation (dimensionless)
