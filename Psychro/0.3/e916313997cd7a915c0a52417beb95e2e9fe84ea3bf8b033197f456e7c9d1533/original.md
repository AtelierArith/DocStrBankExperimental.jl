```
entropym(DryAir, T, P[, out_unit=u"m^3/kg"])
entropym(Vapor, T[, out_unit=u"m^3/kg"])
entropym(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

Calculates the molar entropy of a gas. In the case of moist air, parameters specifying the humidity shoud be added. 

If `Unitful` units are used, all parameters of the function (except dimensionless) should have units associated. When no units are provided, all parameters should use SI units (and so does the return type). For further information, checkout the doc for `Psychro` module.

Temperature should be in the range `173.15 K < T < 473.15` and pressure should be below 5 MPa.

# Examples

```julia-repl
julia> entropym(DryAir, 293.15, 101325.0)
2.0590912665460226

julia> entropym(DryAir, 20.0u"°C", 1.0u"atm")
2.0590912665460226 J K^-1 mol^-1

julia> entropy(Vapor, 293.15)
8665.873003613997

julia> entropym(Vapor, 20.0u"°C")
156.11812860454717 J K^-1 mol^-1

julia> entropym(MoistAir, 293.15, RelHum, 0.7, 101325.0)
4.739496639035868

julia> entropym(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
5.197949865380578 J K^-1 mol^-1

julia> entropym(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"kJ/kmol/°F")
2.8877499252114327 °F^-1 kJ kmol^-1

```
