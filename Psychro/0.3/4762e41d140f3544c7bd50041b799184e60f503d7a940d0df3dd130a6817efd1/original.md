```
enthalpy(DryAir, T, P[, out_unit=u"m^3/kg"])
enthalpy(Vapor, T[, out_unit=u"m^3/kg"])
enthalpy(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

Calculates the specific enthalpy of a gas. In the case of moist air, parameters specifying the humidity shoud be added and the the property is based on the mass of dry air not mass of the gas (as is the case for `DryAir` or `Vapor`). 

If `Unitful` units are used, all parameters of the function (except dimensionless) should have units associated. When no units are provided, all parameters should use SI units (and so does the return type). For further information, checkout the doc for `Psychro` module.

Temperature should be in the range `173.15 K < T < 473.15` and pressure should be below 5 MPa.

# Examples

```julia-repl
julia> enthalpy(DryAir, 293.15, 101325.0)
20121.2722813185

julia> enthalpy(DryAir, 20.0u"°C", 1.0u"atm")
20121.2722813185 kg^-1 J

julia> enthalpy(Vapor, 293.15)
2.5374003352412493e6

julia> enthalpy(Vapor, 20.0u"°C")
2.5374003352412493e6 kg^-1 J

julia> enthalpy(MoistAir, 293.15, RelHum, 0.7, 101325.0)
46142.773129687484

julia> enthalpy(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
50944.84575377501 kg^-1 J

julia> enthalpy(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"J/lb")
23108.193324739244 J lb^-1

```
