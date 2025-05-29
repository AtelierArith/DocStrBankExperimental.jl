```
CharUnits = SI_units(length=1000m, temperature=1000K, stress=10Pa, viscosity=1e20)
```

Specify the characteristic values using SI units

# Examples:

```julia-repl
julia> CharUnits = SI_units(length=1000m)
Employing SI units
Characteristic values:
         length:      1000 m
         time:        1.0e19 s
         stress:      10 Pa
         temperature: 1000.0 K
```

Note that the same can be achieved if the input is given in `km`:

```julia-repl
julia> CharUnits = SI_units(length=1km)
```
