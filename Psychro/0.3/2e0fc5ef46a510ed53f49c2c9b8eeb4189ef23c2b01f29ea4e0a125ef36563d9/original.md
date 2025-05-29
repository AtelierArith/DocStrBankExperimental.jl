Type used to model moist air

This uses the formulations presente in the ASHRAE handbook Psychrometrics: Theory and Practice, reference [5]. 

The temperature range is `173.15 < T < 474.15 K` with pressures `P < 5 MPa`.

The methods dealing with this type implement the equations of references [1-2] to calculate some thermodynamics of real moits air.

Some thermodynamic properties are implemented as methods. Every method takes as arguments, the type `MoistAir` as first argument, temperature as second argument, a type declaring how humidity is specified, the value of humidity using and pressure. If `Unitful` package is used, any unit can be used. On the other hand if no units are provided, the packages assumes SI units all through. In particular:

  * Temperature in K
  * Pressure in Pa
  * Length in m
  * Quantity of matter in mol
  * Mass in kg
  * Energy in J

To specify humidity the following types are implemented:

  * `WetBulb` for wet bulb temperature, actually adiabatic saturation temperature
  * `DewPoint` Dew point temperature
  * `RelHum` Relative humidity
  * `HumRat` Humidity ratio (kg of vapor / kg of dry air)
  * `SpecHum` Specific humidity (kg of vapor / kg of moist air)
  * `MolarFrac` Molar fraction of water vapor.

The following methods are implemented:

  * `volume(MoistAir, T, HumType, h, P)` specific volume
  * `volumem(MoistAir, T, HumType, h, P` molar volume
  * `density(MoistAir, T, HumType, h, P)` density
  * `enthalpy(MoistAir, T, HumType, h, P)` specific enthalpy
  * `enthalpym(MoistAir, T, HumType, h, P)` molar enthalpy
  * `entropy(MoistAir, T, HumType, h, P)` specific entropy
  * `entropym(MoistAir, T, HumType, h, P)` molar entropy
  * `compressfactor(MoistAir, T, HumType, h, P)` Compressibility factor.

It should be noted that the specific enthalpy, entropy and volume are calculated with respect to the mass of dry air. Therefore, 1 J/kg is actually 1 J per kg of dry air.
