```
compressfactor(DryAir, T, P[, out_unit=u"m^3/kg"])
compressfactor(Vapor, T[, out_unit=u"m^3/kg"])
compressfactor(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

Calculates the compressibility factor Z of a gas. In the case of moist air, parameters specifying the humidity shoud be added. 

If `Unitful` units are used, all parameters of the function (except dimensionless) should have units associated. When no units are provided, all parameters should use SI units (and so does the return type). For further information, checkout the doc for `Psychro` module.

Temperature should be in the range `173.15 K < T < 473.15` and pressure should be below 5 MPa.

# Examples

```julia-repl
julia> compressfactor(DryAir, 293.15, 101325.0)
1.2044776705391136

julia> compressfactor(DryAir, 20.0u"°C", 1.0u"atm")
1.2044776705391136 kg m^-3

julia> compressfactor(Vapor, 293.15)
0.017308548277505224

julia> compressfactor(Vapor, 20.0u"°C")
0.017308548277505224 kg m^-3

julia> compressfactor(MoistAir, 293.15, RelHum, 0.7, 101325.0)
1.1971436091840653

julia> compressfactor(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
1.195819185774941 kg m^-3

```
