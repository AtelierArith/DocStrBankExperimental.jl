```Julia
lambert(U::UnitSystem) = luminance(𝟐/turn(U),U,Gauss)
```

歴史的単位の `luminance` (nt)。

```Julia
julia> lambert(Engineering) # nt
3183.098861837906

julia> lambert(MetricDegree) # lm⋅m⁻²deg⁻²
0.01692318998815047

julia> lambert(MetricGradian) # lm⋅m⁻²gon⁻²
0.012337005501361699

julia> lambert(CGS) # sb
0.3183098861837907

julia> lambert(English) # fc
295.7195608852815
```
