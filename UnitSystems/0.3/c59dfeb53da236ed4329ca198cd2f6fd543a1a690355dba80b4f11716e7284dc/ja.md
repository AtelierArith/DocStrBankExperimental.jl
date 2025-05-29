```Julia
inchmercury(U::UnitSystem) = pressure(inHg,U,Metric)
```

標準大気条件下で1インチの水銀によって加えられる`pressure`の単位。

```Julia
juila> inchmercury(Metric) # Pa
0.0002952998016471232

julia> inchmercury(English) # lb⋅ft⁻²
6.1674645863632695e-6

julia> inchmercury(IPS) # lb⋅in⁻²
4.2829615183078284e-8
```
