Type used to model dry air

This uses the formulations presente in the ASHRAE handbook Psychrometrics: Theory and Practice, reference [5].

The methods dealing with this type implement the equations of reference [2].

Some thermodynamic properties are implemented as methods. Every method takes as arguments, the type Vapor`as first argument and the temperature as the second. If`Unitful` package is used, any unit can be used. On the other hand if no units are provided, the packages assumes SI units all through. In particular:

  * Temperature in K
  * Pressure in Pa
  * Length in m
  * Quantity of matter in mol
  * Mass in kg
  * Energy in J

The following methods are implemented:

  * `volume(DryAir, T, P)` specific volume
  * `volumem(DryAir, T, P` molar volume
  * `density(DryAir, T, P)` density
  * `enthalpy(DryAir, T, P)` specific enthalpy
  * `enthalpym(DryAir, T, P)` molar enthalpy
  * `entropy(DryAir, T, P)` specific entropy
  * `entropym(DryAir, T, P)` molar entropy
  * `compressfactor(DryAir, T, P)` Compressibility factor.
