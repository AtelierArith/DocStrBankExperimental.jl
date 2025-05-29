```
density(DryAir, T, P[, out_unit=u"m^3/kg"])
density(Vapor, T[, out_unit=u"m^3/kg"])
density(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

Calculates the density volume of a gas. In the case of moist air, parameters specifying the humidity shoud be added. 

If `Unitful` units are used, all parameters of the function (except dimensionless) should have units associated. When no units are provided, all parameters should use SI units (and so does the return type). For further information, checkout the doc for `Psychro` module.

Temperature should be in the range `173.15 K < T < 473.15` and pressure should be below 5 MPa.

# Examples

```julia-repl
julia> density(DryAir, 293.15, 101325.0)
1.2044776705391136

julia> density(DryAir, 20.0u"°C", 1.0u"atm")
1.2044776705391136 kg m^-3

julia> density(Vapor, 293.15)
0.017308548277505224

julia> density(Vapor, 20.0u"°C")
0.017308548277505224 kg m^-3

julia> density(MoistAir, 293.15, RelHum, 0.7, 101325.0)
1.1971436091840653

julia> density(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
1.195819185774941 kg m^-3

julia> density(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"lb/inch^3")
4.3201708903793606e-5 in^-3 lb

```
