Parameter state for Chaboche material.

The classical viscoplastic material is a special case of this model with `C1 = C2 = 0`.

  * `E`: Young's modulus
  * `nu`: Poisson's ratio
  * `R0`: initial yield strength
  * `Kn`: plasticity multiplier divisor (drag stress)
  * `nn`: plasticity multiplier exponent
  * `C1`, `D1`: parameters governing behavior of backstress X1
  * `C2`, `D2`: parameters governing behavior of backstress X2
  * `Q`: hardening saturation state
  * `b`: rate of convergence to hardening saturation
