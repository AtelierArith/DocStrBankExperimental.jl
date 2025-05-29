```Julia
barye(U::UnitSystem) = pressure(𝟏,U,Gauss)
```

圧力の歴史的単位 (Pa または lb⋅ft⁻²)。

```Julia
julia> barye(Metric) # Pa
0.09999999999999996

julia> barye(English) # lb⋅ft⁻²
0.002088543423315013

julia> barye(IPS) # lb⋅in⁻²
1.4503773773020932e-5
```
