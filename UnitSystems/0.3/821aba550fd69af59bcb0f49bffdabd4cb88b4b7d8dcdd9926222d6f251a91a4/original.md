```Julia
psi(U::UnitSystem) = pressure(𝟏,U,IPS)
```

English unit of `pressure` (Pa or lb⋅ft⁻²).

```Julia
julia> psi(Metric) # Pa
6894.757293168356

julia> psi(English) # lb⋅ft⁻²
143.99999999999997

julia> psi(IPS) # lb⋅in⁻²
1
```
