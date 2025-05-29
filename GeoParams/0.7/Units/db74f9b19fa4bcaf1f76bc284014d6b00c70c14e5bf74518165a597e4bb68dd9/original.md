```
GEO_units(;length=1000km, temperature=1000C, stress=10MPa, viscosity=1e20Pas)
```

Creates a non-dimensionalization object using GEO units.

GEO units implies that upon dimensionalization, `time` will be in `Myr`, `length` in `km`, stress in `MPa`, etc. which is more convenient for typical geodynamic simulations than SI units The characteristic values given as input can be in arbitrary units (`km` or `m`), provided the unit is specified.

# Examples:

```julia-repl
julia> CharUnits = GEO_units()
Employing GEO units
Characteristic values:
         length:      1000 km
         time:        0.3169 Myr
         stress:      10 MPa
         temperature: 1000.0 °C
julia> CharUnits.velocity
1.0e-7 m s⁻¹
```

If we instead have a crustal-scale simulation, it is likely more appropriate to use a different characteristic `length`:

```julia-repl
julia> CharUnits = GEO_units(length=10km)
Employing GEO units
Characteristic values:
         length:      10 km
         time:        0.3169 Myr
         stress:      10 MPa
         temperature: 1000.0 °C
```
