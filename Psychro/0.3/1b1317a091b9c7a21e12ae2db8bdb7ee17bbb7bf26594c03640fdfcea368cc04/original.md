```
entropy(DryAir, T, P[, out_unit=u"m^3/kg"])
entropy(Vapor, T[, out_unit=u"m^3/kg"])
entropy(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

Calculates the specific entropy of a gas. In the case of moist air, parameters specifying the humidity shoud be added and the the property is based on the mass of dry air not mass of the gas (as is the case for `DryAir` or `Vapor`). 

If `Unitful` units are used, all parameters of the function (except dimensionless) should have units associated. When no units are provided, all parameters should use SI units (and so does the return type). For further information, checkout the doc for `Psychro` module.

Temperature should be in the range `173.15 K < T < 473.15` and pressure should be below 5 MPa.

# Examples

```julia-repl
julia> entropy(DryAir, 293.15, 101325.0)
71.09262577195514

julia> entropy(DryAir, 20.0u"°C", 1.0u"atm")
71.09262577195514 kg^-1 J K^-1

julia> entropy(Vapor, 293.15)
8665.873003613997

julia> entropy(Vapor, 20.0u"°C")
8665.873003613997 kg^-1 J K^-1

julia> entropy(MoistAir, 293.15, RelHum, 0.7, 101325.0)
166.33538729355692

julia> entropy(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
182.97140931650105 kg^-1 J K^-1

julia> entropy(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"kJ/lb/°F")
0.04610801955228433 °F^-1 kJ lb^-1

```
