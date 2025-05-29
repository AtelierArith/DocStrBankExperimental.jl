```Julia
grain(U::UnitSystem) = milli(U)*pound(U)/𝟕
```

理想的な穀物の種子、`質量`の単位（kgまたはlb）。

```Julia
julia> grain(Metric) # kg
6.479891000000001e-5

julia> grain(CGS) # g
0.06479891000000002

julia> grain(English) # lb
0.00014285714285714287

julia> grain(QCD) # mₚ
3.874091872291683e22
```
