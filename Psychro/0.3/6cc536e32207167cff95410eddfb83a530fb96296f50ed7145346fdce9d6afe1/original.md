```
molarfrac(Tk, HumidityType, x, P)
```

Calculates the molarfraction of water vapor given a humidity parameter. The humidity parameter can be one of the following:

  * `MolarFrac` - Identity function basically...
  * `RelHum` - Relative humidity in decimal notation (not percentage!)
  * `DewPoint`- Dew point temperature in K
  * `HumRat` - Humidity ration, kg of vapor / kg of dry air
  * `SpecHum` - Specific Humidity of water vapor = mv / (mv + ma)
  * `WetBulb` - Wet bulb temperature in K- estimated by the adiabatic saturation temperature.

As usual all calculations are performed using plain SI units.  The parameters used by this function are:

  * `Tk` - Temperature in K
  * Humidity type - a type listed above that characterizes the humidity
  * The value of the humidity parameter.
  * P - Pressure in Pa
