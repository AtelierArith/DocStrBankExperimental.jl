Parameter state for Memory material.

  * `E`: Young's modulus
  * `nu`: Poisson's ratio
  * `R0`: initial yield strength
  * `Kn`: plasticity multiplier divisor (drag stress)
  * `nn`: plasticity multiplier exponent
  * `C1`, `D1`: parameters governing behavior of backstress X1
  * `C2`, `D2`: parameters governing behavior of backstress X2
  * `Q0`: The initial isotropic hardening saturation value. Has the units of stress.
  * `QM`: The asymptotic isotropic hardening saturation value reached with high strain amplitude.

    Has the units of stress.
  * `mu`: Controls the rate of evolution of the strain-amplitude dependent isotropic hardening saturation value.
  * `b`: Controls the rate of evolution for isotropic hardening.
  * `eta`: Controls the balance between memory surface kinematic and isotropic hardening.

    Dimensionless, support `[0,1]`. At `0`, the memory surface hardens kinematically. At `1`, the memory surface hardens isotropically.

    Initially, the value `1/2` was used by several authors. Later, values `< 1/2` have been suggested to capture the progressive process of memorization.
  * `m`: memory evanescence exponent. Controls the non-linearity of the memory evanescence.
  * `pt`: threshold of equivalent plastic strain, after which the memory evanescence starts.
  * `xi`: memory evanescence strength multiplier.
