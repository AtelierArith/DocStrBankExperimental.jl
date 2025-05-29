```Julia
joule(U::UnitSystem) = energy(𝟏,U,Metric)
```

エネルギーのメトリック単位 (J または lb⋅ft)。

```Julia
julia> joule(Metric) # J
1

julia> joule(CGS) # erg
1.0e7

julia> joule(British) # lb⋅ft
0.7375621492772654
```
