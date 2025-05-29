```
CharUnits = NO_units(length=1, temperature=1, stress=1, viscosity=1)
```

無次元単位での特性値を指定します

# 例:

```julia-repl
julia> using GeoParams;
julia> CharUnits = NO_units()
NONE単位を使用しています
特性値:
         length:      1
         time:        1.0
         stress:      1
         temperature: 1.0
```
