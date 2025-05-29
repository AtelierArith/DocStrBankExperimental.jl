Parameter state for DSA (dynamic strain aging) material.

This is similar to the Chaboche model, but with additional static recovery terms.

Parameters:

  * `E`: Young's modulus
  * `nu`: Poisson's ratio
  * `R0`: initial yield strength
  * `Kn`: plasticity multiplier divisor (drag stress)
  * `nn`: plasticity multiplier exponent
  * `C1`, `D1`: parameters governing behavior of backstress X1
  * `C2`, `D2`: parameters governing behavior of backstress X2
  * `Q`: shift parameter for yield strength evolution
  * `b`: multiplier for yield strength evolution
  * `w`: controls the average waiting time a dislocation is arrested at localized obstacles.

    It represents a strain increment produced when all arrested dislocations overcome localized obstacles, and move toward the next pinned configuration.

    In practice, this parameter controls how fast the effective aging time reacts to plastic flow: $\dot{t}_a = 1 - t_a \dot{p} / w$
  * `P1`, `P2`: controls the maximum hardening in the fully aged state.

    Has the units of stress.
  * `m`: controls the characteristic diffusion time. Depends on the type of diffusion.

    The value `1/3` is thought to represent pipe diffusion along dislocation lines. Another typical value is `2/3`.
  * `m1`, `m2`: The exponent of the power-law type static recovery of backstresses.

    The static recovery mechanism becomes activated at higher temperatures.

    This parameter controls the secondary creep and constant slope relaxation of stresses over a longer period of time. Higher values (>6..10) effectively deactivate static recovery, whereas lower values (<5) activate it.
  * `M1`, `M2`: The normalizer of the power-law type static recovery of backstresses.

    Has the units of stress. Can be used to activate/deactivate static recovery. Deactivation occurs with high values.
  * `ba`: Controls the rate of evolution of aging stress to its asymptotic value.

    Dimensionless. Similar to the isotropic hardening `b`.
  * `xi`: Controls the magnitude of the Marquis effect from the aging stress.

    The Marquis effect is that increased hardening due to aging shows as increased relaxation.

    Dimensionless. Support `[0,1]`.

    At `0`, the aging stress contributes solely to the size of the yield surface `R` (isotropic hardening).

    At `1`, the aging stress contributes solely to the viscoplastic drag stress `K`.
