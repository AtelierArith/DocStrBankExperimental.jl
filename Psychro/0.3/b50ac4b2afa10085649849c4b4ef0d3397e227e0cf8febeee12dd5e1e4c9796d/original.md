Type used to model saturated water vapor

This uses the formulations presente in the ASHRAE handbook Psychrometrics: Theory and Practice, reference [5].

The methods dealing with this type implement the equations of reference [1].

Some thermodynamic properties are implemented as methods. Every method takes as arguments, the type `DryAir` as first argument and the saturation temperature. If `Unitful` package is used, any unit can be used. On the other hand if no units are provided, the packages assumes SI units all through. In particular:

  * Temperature in K
  * Pressure in Pa
  * Length in m
  * Quantity of matter in mol
  * Mass in kg
  * Energy in J

The following methods are implemented:

  * `volume(Vapor, T)` specific volume
  * `volumem(Vapor, T)` molar volume
  * `density(Vapor, T)` density
  * `enthalpy(Vapor, T)` specific enthalpy
  * `enthalpym(Vapor, T)` molar enthalpy
  * `entropy(Vapor, T)` specific entropy
  * `entropym(Vapor, T)` molar entropy
  * `compressfactor(Vapor, T)` Compressibility factor.
