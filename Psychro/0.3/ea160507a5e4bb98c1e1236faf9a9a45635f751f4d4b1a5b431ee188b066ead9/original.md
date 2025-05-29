```
volumem(DryAir, T, P[, out_unit=u"m^3/kg"])
volumem(Vapor, T[, out_unit=u"m^3/kg"])
volumem(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

Calculates the molar volume of a gas. In the case of moist air, parameters specifying the humidity shoud be added. 

If `Unitful` units are used, all parameters of the function (except dimensionless) should have units associated. When no units are provided, all parameters should use SI units (and so does the return type). For further information, checkout the doc for `Psychro` module.

Temperature should be in the range `173.15 K < T < 473.15` and pressure should be below 5 MPa.

# Examples

```julia-repl
julia> volumem(DryAir, 293.15, 101325.0)
0.024046522993685877

julia> volumem(DryAir, 20.0u"°C", 1.0u"atm")
0.024046522993685877 m^3 mol^-1

julia> volumem(Vapor, 293.15)
1.040831369053248

julia> volumem(Vapor, 20.0u"°C")
1.040831369053248 m^3 mol^-1

julia> volumem(MoistAir, 293.15, RelHum, 0.7, 101325.0)
0.02404547233948706

julia> volumem(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
0.024045209859305458 m^3 mol^-1

julia> volumem(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"inch^3/mol")
1467.32873315839 in^3 mol^-1
```
