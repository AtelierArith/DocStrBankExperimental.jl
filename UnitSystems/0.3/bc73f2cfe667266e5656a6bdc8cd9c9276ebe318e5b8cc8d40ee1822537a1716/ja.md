```Julia
yard(U::UnitSystem) = 𝟑*foot(U)
```

英語の単位 `length` (m または ft)。

```Julia
julia> yard(Metric) # m
0.9144000000000001

julia> yard(English) # ft
3

julia> yard(IPS) # in
35.999999999999986
```
