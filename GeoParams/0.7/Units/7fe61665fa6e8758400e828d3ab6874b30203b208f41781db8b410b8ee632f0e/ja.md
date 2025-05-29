```
CharUnits = SI_units(length=1000m, temperature=1000K, stress=10Pa, viscosity=1e20)
```

SI単位を使用して特性値を指定します

# 例:

```julia-repl
julia> CharUnits = SI_units(length=1000m)
SI単位を使用しています
特性値:
         length:      1000 m
         time:        1.0e19 s
         stress:      10 Pa
         temperature: 1000.0 K
```

入力が `km` で与えられた場合も同様のことが達成できます:

```julia-repl
julia> CharUnits = SI_units(length=1km)
```
