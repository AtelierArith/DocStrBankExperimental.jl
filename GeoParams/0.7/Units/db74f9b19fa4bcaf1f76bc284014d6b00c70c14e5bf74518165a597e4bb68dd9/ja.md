```
GEO_units(;length=1000km, temperature=1000C, stress=10MPa, viscosity=1e20Pas)
```

GEO単位を使用して無次元化オブジェクトを作成します。

GEO単位は、次元化すると`time`が`Myr`、`length`が`km`、`stress`が`MPa`などになることを意味し、これはSI単位よりも典型的な地球力学シミュレーションにとって便利です。入力として与えられる特性値は、単位が指定されていれば任意の単位（`km`または`m`）であることができます。

# 例:

```julia-repl
julia> CharUnits = GEO_units()
GEO単位を使用しています
特性値:
         length:      1000 km
         time:        0.3169 Myr
         stress:      10 MPa
         temperature: 1000.0 °C
julia> CharUnits.velocity
1.0e-7 m s⁻¹
```

もし、地殻スケールのシミュレーションを行う場合、異なる特性の`length`を使用する方が適切である可能性があります:

```julia-repl
julia> CharUnits = GEO_units(length=10km)
GEO単位を使用しています
特性値:
         length:      10 km
         time:        0.3169 Myr
         stress:      10 MPa
         temperature: 1000.0 °C
```
