```Julia
psi(U::UnitSystem) = pressure(𝟏,U,IPS)
```

圧力の英単位（Paまたはlb⋅ft⁻²）。

```Julia
julia> psi(Metric) # Pa
6894.757293168356

julia> psi(English) # lb⋅ft⁻²
143.99999999999997

julia> psi(IPS) # lb⋅in⁻²
1
```
