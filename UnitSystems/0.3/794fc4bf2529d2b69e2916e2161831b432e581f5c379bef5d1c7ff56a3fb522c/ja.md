```Julia
stilb(U::UnitSystem) = luminance(𝟏,U,Gauss)
```

歴史的単位の `luminance` (lx⋅rad⁻²)。

```Julia
julia> stilb(Engineering) # nt
9999.999999999996

julia> stilb(MetricDegree) # lm⋅m⁻²deg⁻²
3.046174197867084

julia> stilb(MetricGradian) # lm⋅m⁻²gon⁻²
2.4674011002723395

julia> stilb(CGS) # sb
1

julia> stilb(English) # fc
929.0303999999999
```
