```Julia
ips(U::UnitSystem) = inch(U)/second(U)
```

インチ毎秒の単位 `speed` (m⋅s⁻¹ または ft⋅s⁻¹)。

```Julia
julia> ips(CGS) # cm⋅s⁻¹
2.5400000000000005

julia> ips(English) # ft⋅s⁻¹
0.08333333333333334
```
