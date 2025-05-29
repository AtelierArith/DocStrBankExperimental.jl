```
volume(DryAir, T, P[, out_unit=u"m^3/kg"])
volume(Vapor, T[, out_unit=u"m^3/kg"])
volume(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

Calculates the specific volume of a gas. In the case of moist air, parameters specifying the humidity shoud be added and the the property is based on the mass of dry air not mass of the gas (as is the case for `DryAir` or `Vapor`). 

If `Unitful` units are used, all parameters of the function (except dimensionless) should have units associated. When no units are provided, all parameters should use SI units (and so does the return type). For further information, checkout the doc for `Psychro` module.

Temperature should be in the range `173.15 K < T < 473.15` and pressure should be below 5 MPa.

# Examples

```julia-repl
julia> volume(DryAir, 293.15, 101325.0)
0.8302353995092402

julia> volume(DryAir, 20.0u"°C", 1.0u"atm")
0.8302353995092402 kg^-1 m^3

julia> volume(Vapor, 293.15)
57.77492045936827

julia> volume(Vapor, 20.0u"°C")
57.77492045936827 kg^-1 m^3

julia> volume(MoistAir, 293.15, RelHum, 0.7, 101325.0)
0.843889817602806

julia> volume(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
0.8464079202783964 kg^-1 m^3

julia> volume(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"inch^3/lb")
23428.490579267214 in^3 lb^-1
```
