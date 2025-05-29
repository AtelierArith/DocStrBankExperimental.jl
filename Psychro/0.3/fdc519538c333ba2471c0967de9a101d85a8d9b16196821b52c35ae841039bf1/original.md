```
enthalpym(DryAir, T, P[, out_unit=u"m^3/kg"])
enthalpym(Vapor, T[, out_unit=u"m^3/kg"])
enthalpym(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

Calculates the molar enthalpy of a gas. In the case of moist air, parameters specifying the humidity shoud be added. 

If `Unitful` units are used, all parameters of the function (except dimensionless) should have units associated. When no units are provided, all parameters should use SI units (and so does the return type). For further information, checkout the doc for `Psychro` module.

Temperature should be in the range `173.15 K < T < 473.15` and pressure should be below 5 MPa.

# Examples

```julia-repl
julia> enthalpym(DryAir, 293.15, 101325.0)
582.7824697199684

julia> enthalpym(DryAir, 20.0u"°C", 1.0u"atm")
582.7824697199684 J mol^-1

julia> enthalpy(Vapor, 293.15)
2.5374003352412493e6

julia> enthalpym(Vapor, 20.0u"°C")
45711.977511464975 J mol^-1

julia> enthalpym(MoistAir, 293.15, RelHum, 0.7, 101325.0)
1314.7744549269437

julia> enthalpym(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
1447.2684837312868 J mol^-1

julia> enthalpym(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"kJ/kmol")
1447.2684837312868 kJ kmol^-1

```
